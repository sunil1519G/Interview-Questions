# Contributing Guide

Thanks for improving this interview preparation repository.

## Branch Naming

Use clear branch names:
- `topic/<area>-<short-description>`
- `fix/<area>-<short-description>`
- `docs/<area>-<short-description>`

Examples:
- `topic/java-streams-basic`
- `topic/microservices-circuit-breaker`

## Content Rules

- One concept per markdown file.
- Follow `templates/question-template.md`.
- Keep answers technically correct and interview-focused.
- Include at least one code snippet unless the topic is purely conceptual.
- Add tags and related questions.

## Pull Request Checklist

Before opening a PR, confirm:
- [ ] File is placed in the correct difficulty and topic folder.
- [ ] The topic `README.md` includes a link to the new file.
- [ ] The question format follows the template.
- [ ] Code snippets are readable and contextually correct.
- [ ] Spelling and markdown formatting are checked.

## Review Expectations

Reviewers verify:
- Technical accuracy
- Clarity of explanation
- Difficulty alignment
- Practical usefulness in interviews

## Maintenance Standards

- Prefer updates over duplication when a similar question already exists.
- Keep tags consistent (for example: `java`, `collections`, `threading`, `spring-security`, `resilience`).
- If a concept evolves, revise existing answers with a short "Last updated" note.
