# Spring Boot Interview Questions (Advanced)

Source PDF: `Springboot Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. How do you secure Spring Boot APIs in production environments?](#q-1)
<a id="q-1"></a>
## 1. Question
How do you secure Spring Boot APIs in production environments?

### Answer
Implement layered security: (1) HTTPS/TLS: encrypt all traffic. (2) Authentication: OAuth2 (for third-party access), JWT (for stateless APIs), or sessions (for web apps). (3) Authorization: role-based access control (RBAC) via @PreAuthorize. (4) API security: rate limiting, CORS configuration, input validation. (5) Secrets management: externalize API keys, DB passwords via environment variables or vault services (HashiCorp Vault, AWS Secrets Manager). (6) Security headers: HSTS, X-Frame-Options, CSP. (7) Monitoring: log security events, track failed auth attempts. Spring Security provides annotation-based access control and OAuth2 provider integration.

### Code Snippet
```java
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.method.configuration.EnableGlobalMethodSecurity;
import org.springframework.security.oauth2.jwt.JwtDecoder;
import org.springframework.web.filter.CorsFilter;
import org.springframework.context.annotation.Bean;

// 1. Security Configuration with OAuth2 JWT
@Configuration
@EnableGlobalMethodSecurity(prePostEnabled = true)
public class SecurityConfig {
    
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            // HTTPS enforcement
            .requiresChannel()
                .anyRequest()
                .requiresSecure() // force HTTPS
            .and()
            
            // CORS configuration
            .cors()
            .and()
            
            // CSRF protection (disable for stateless APIs)
            .csrf().disable()
            
            // Authorization rules
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // unauthenticated access
                .antMatchers("/admin/**").hasRole("ADMIN") // RBAC
                .antMatchers("/api/**").authenticated() // requires auth
                .anyRequest().authenticated()
            .and()
            
            // OAuth2 Resource Server with JWT
            .oauth2ResourceServer()
                .jwt()
                    .jwtAuthenticationConverter(jwtAuthenticationConverter())
            .and()
            .and()
            
            // Security headers
            .headers()
                .frameOptions().deny() // prevent clickjacking
                .xssProtection()
                .and()
                .cacheControl(); // prevent caching sensitive data
        
        return http.build();
    }
    
    // JWT Authentication Converter: extract roles from JWT claims
    private JwtAuthenticationConverter jwtAuthenticationConverter() {
        JwtGrantedAuthoritiesConverter authoritiesConverter = new JwtGrantedAuthoritiesConverter();
        authoritiesConverter.setAuthoritiesClaimName("roles");
        authoritiesConverter.setAuthorityPrefix("ROLE_");
        
        JwtAuthenticationConverter converter = new JwtAuthenticationConverter();
        converter.setJwtGrantedAuthoritiesConverter(authoritiesConverter);
        return converter;
    }
    
    @Bean
    public CorsFilter corsFilter() {
        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        CorsConfiguration config = new CorsConfiguration();
        config.setAllowCredentials(true);
        config.addAllowedOrigin("https://trusted-domain.com"); // whitelist origins
        config.addAllowedMethod("GET");
        config.addAllowedMethod("POST");
        config.addAllowedMethod("PUT");
        config.addAllowedMethod("DELETE");
        config.addAllowedHeader("*");
        source.registerCorsConfiguration("/**", config);
        return new CorsFilter(source);
    }
}

// 2. JWT Token Provider
@Component
public class JwtTokenProvider {
    
    @Value("${jwt.secret}") // externalized secret
    private String jwtSecret;
    
    @Value("${jwt.expiration}") // externalized expiration
    private int jwtExpiration;
    
    public String generateToken(String userId, List<String> roles) {
        long nowMillis = System.currentTimeMillis();
        long expMillis = nowMillis + jwtExpiration;
        
        return Jwts.builder()
            .setSubject(userId)
            .claim("roles", roles) // embed roles in JWT
            .setIssuedAt(new Date(nowMillis))
            .setExpiration(new Date(expMillis))
            .signWith(SignatureAlgorithm.HS512, jwtSecret) // sign with secret
            .compact();
    }
    
    public String getUserIdFromToken(String token) {
        return Jwts.parser()
            .setSigningKey(jwtSecret)
            .parseClaimsJws(token)
            .getBody()
            .getSubject();
    }
}

// 3. Controller with Authorization
@RestController
@RequestMapping("/api/orders")
public class OrderController {
    
    // Public endpoint: no auth required
    @GetMapping("/public/featured")
    public List<Order> getFeaturedOrders() {
        return orderService.getFeaturedOrders();
    }
    
    // Authenticated: any logged-in user
    @GetMapping("/{id}")
    @PreAuthorize("isAuthenticated()")
    public Order getOrder(@PathVariable Long id) {
        return orderService.getOrder(id);
    }
    
    // Admin only: role-based access
    @DeleteMapping("/{id}")
    @PreAuthorize("hasRole('ADMIN')")
    public ResponseEntity<?> deleteOrder(@PathVariable Long id) {
        orderService.delete(id);
        return ResponseEntity.ok("Order deleted");
    }
    
    // Owner check: user can only access own orders
    @GetMapping("/my-orders")
    @PreAuthorize("isAuthenticated()")
    public List<Order> getMyOrders(Authentication authentication) {
        String userId = authentication.getName();
        return orderService.getOrdersByUserId(userId);
    }
}

// 4. Input Validation: prevent injection attacks
@RestController
@RequestMapping("/api/users")
public class UserController {
    
    @PostMapping
    public ResponseEntity<?> createUser(@Valid @RequestBody UserCreateRequest request) {
        // @Valid triggers validation on UserCreateRequest fields
        User user = userService.create(request.getName(), request.getEmail());
        return ResponseEntity.created(URI.create("/api/users/" + user.getId())).body(user);
    }
}

public class UserCreateRequest {
    @NotBlank(message = "Name cannot be blank")
    @Size(min = 2, max = 100)
    private String name;
    
    @NotBlank(message = "Email cannot be blank")
    @Email(message = "Email should be valid")
    private String email;
    
    // getters/setters
}

// 5. Rate Limiting: prevent brute force attacks
@Configuration
public class RateLimitConfig {
    
    @Bean
    public RateLimiter rateLimiter() {
        // Allow 100 requests per minute per user
        return RateLimiter.create(100.0 / 60.0);
    }
}

@Component
public class RateLimitInterceptor implements HandlerInterceptor {
    
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) {
        String userId = SecurityContextHolder.getContext().getAuthentication().getName();
        
        if (!rateLimiter.tryAcquire()) {
            response.setStatus(HttpStatus.TOO_MANY_REQUESTS.value());
            return false;
        }
        return true;
    }
}

// 6. Audit Logging: track security-relevant events
@Component
public class AuditLogger {
    
    private static Logger logger = LoggerFactory.getLogger("AUDIT");
    
    public void logLoginAttempt(String userId, boolean success) {
        logger.info("LOGIN_ATTEMPT: userId={}, success={}, timestamp={}", 
            userId, success, System.currentTimeMillis());
    }
    
    public void logUnauthorizedAccess(String userId, String resource) {
        logger.warn("UNAUTHORIZED_ACCESS: userId={}, resource={}, timestamp={}", 
            userId, resource, System.currentTimeMillis());
    }
}

// 7. Secrets Management: externalize sensitive data
@Configuration
public class SecretsConfig {
    
    @Value("${db.password}") // from environment variable or vault
    private String dbPassword;
    
    @Value("${api.key}") // never hardcode secrets
    private String apiKey;
    
    @Bean
    public DataSource dataSource() {
        // dbPassword is read from environment, not from code
        DriverManagerDataSource ds = new DriverManagerDataSource();
        ds.setPassword(dbPassword);
        return ds;
    }
}
```

### Keywords/Tags
- spring-boot
- advanced
- security

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
