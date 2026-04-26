# Low Level Design Interview Questions (Intermediate)

Source PDF: `Low Level Design Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. How to prepare for Low-Level Design Interviews?](#q-1)
- [2. How to Solve Low-Level Design problems in Interviews?](#q-2)
- [3. How to design Snake and Ladder?](#q-3)
<a id="q-1"></a>
## 1. Question
How to prepare for Low-Level Design Interviews?

### Answer
For "How to prepare for Low-Level Design Interviews?", explain class responsibilities, interfaces, object interactions, and extensibility points. Mention SOLID-driven trade-offs and how the design remains testable and maintainable.

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- low-level-design
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
How to Solve Low-Level Design problems in Interviews?

### Answer
For "How to Solve Low-Level Design problems in Interviews?", explain class responsibilities, interfaces, object interactions, and extensibility points. Mention SOLID-driven trade-offs and how the design remains testable and maintainable.

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- low-level-design
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
How to design Snake and Ladder?

### Answer
Design Snake & Ladder with clear responsibilities: (1) Board manages cells and snake/ladder positions. (2) Player tracks current position and state. (3) Dice generates random numbers. (4) Game orchestrates turn sequence, validates moves, detects winners. Use Strategy pattern for variable dice rules. Ensure immutability where appropriate (Board definition) and thread-safety if multiplayer. Handle edge cases: exceeding board length (typically no move), landing on snake/ladder, winning conditions.

### Code Snippet
```java
import java.util.*;

// Core entities
public class Player {
    private String name;
    private int position;
    
    public Player(String name) {
        this.name = name;
        this.position = 0; // start at position 0
    }
    
    public void moveForward(int steps) {
        this.position += steps;
    }
    
    public int getPosition() {
        return position;
    }
    
    public String getName() {
        return name;
    }
}

public class Dice {
    private static final int SIDES = 6;
    private Random random = new Random();
    
    public int roll() {
        return random.nextInt(SIDES) + 1; // 1 to 6
    }
}

// Board manages snake and ladder positions
public class Board {
    private static final int BOARD_SIZE = 100;
    private Map<Integer, Integer> snakes;
    private Map<Integer, Integer> ladders;
    
    public Board() {
        this.snakes = new HashMap<>();
        this.ladders = new HashMap<>();
        initializeSnakesAndLadders();
    }
    
    private void initializeSnakesAndLadders() {
        // Snake: from -> to (descending)
        snakes.put(16, 6);
        snakes.put(47, 26);
        snakes.put(49, 11);
        snakes.put(56, 53);
        snakes.put(62, 18);
        snakes.put(87, 24);
        snakes.put(93, 73);
        snakes.put(95, 75);
        snakes.put(98, 79);
        
        // Ladder: from -> to (ascending)
        ladders.put(1, 38);
        ladders.put(4, 14);
        ladders.put(9, 31);
        ladders.put(21, 42);
        ladders.put(28, 84);
        ladders.put(51, 67);
        ladders.put(72, 91);
        ladders.put(80, 99);
    }
    
    public int getFinalPosition(int currentPosition) {
        // If landed on snake, move down
        if (snakes.containsKey(currentPosition)) {
            return snakes.get(currentPosition);
        }
        // If landed on ladder, move up
        if (ladders.containsKey(currentPosition)) {
            return ladders.get(currentPosition);
        }
        // Normal position
        return currentPosition;
    }
    
    public int getBoardSize() {
        return BOARD_SIZE;
    }
}

// Game controller
public class SnakeAndLadderGame {
    private Board board;
    private List<Player> players;
    private Dice dice;
    private int currentPlayerIndex;
    private Player winner;
    
    public SnakeAndLadderGame(List<String> playerNames) {
        this.board = new Board();
        this.dice = new Dice();
        this.players = new ArrayList<>();
        this.currentPlayerIndex = 0;
        this.winner = null;
        
        for (String name : playerNames) {
            players.add(new Player(name));
        }
    }
    
    public void playTurn() {
        if (winner != null) {
            throw new IllegalStateException("Game is already finished");
        }
        
        Player currentPlayer = players.get(currentPlayerIndex);
        int diceRoll = dice.roll();
        
        int newPosition = currentPlayer.getPosition() + diceRoll;
        
        // Validate move (don't exceed board size)
        if (newPosition <= board.getBoardSize()) {
            // Check for snake or ladder
            newPosition = board.getFinalPosition(newPosition);
            currentPlayer.moveForward(newPosition - currentPlayer.getPosition());
            
            // Check win condition
            if (currentPlayer.getPosition() == board.getBoardSize()) {
                this.winner = currentPlayer;
            }
        } else {
            System.out.println("Move exceeds board size, stay at current position");
        }
        
        // Move to next player
        currentPlayerIndex = (currentPlayerIndex + 1) % players.size();
    }
    
    public Player getWinner() {
        return winner;
    }
    
    public List<Player> getPlayers() {
        return new ArrayList<>(players);
    }
}

// Example usage
public class Main {
    public static void main(String[] args) {
        List<String> playerNames = Arrays.asList("Alice", "Bob", "Charlie");
        SnakeAndLadderGame game = new SnakeAndLadderGame(playerNames);
        
        while (game.getWinner() == null) {
            game.playTurn();
        }
        
        System.out.println("Winner: " + game.getWinner().getName());
        System.out.println("Final positions:");
        for (Player p : game.getPlayers()) {
            System.out.println(p.getName() + ": " + p.getPosition());
        }
    }
}
```

### Keywords/Tags
- low-level-design
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
