# AI Coding Agent Instructions

<REPOSITORY_DESCRIPTION> (This is a TypeScript-based repository containing domain logic for a property management operations platform.)

## Approach for Every Task

### 1. Ground Yourself in the Codebase

Before making any changes:

- **Explore the repository structure** to understand the organization
- **Read existing implementations** of similar features or patterns
- **Identify conventions** used in the codebase (naming, file structure, patterns)
- **Find the most relevant files** that relate to your task
- **Understand dependencies** and how modules interact
- Ask: "How is this currently done in this codebase?"

### 2. Research Best Practices

For non-trivial tasks:

- **Search for established patterns** in well-known TypeScript/Node.js projects
- **Look for inspiration** in popular open-source repositories like:
    - NestJS (architecture patterns, dependency injection)
    - TypeORM / Prisma (database patterns)
    - Apollo Server (GraphQL patterns)
    - Yup/Zod (validation patterns)
    - tRPC (type-safe APIs)
    - React Query / TanStack Query (data fetching patterns)
- **Review TypeScript documentation** for language features you're using
- **Consider industry standards** for the domain you're working in
- Ask: "How do leading projects solve this problem?"

### 3. Present a Plan Before Coding

Before writing code, always:

- **Describe your approach** in 2-3 sentences
- **List the files** you'll create or modify
- **Outline the key changes** you'll make
- **Identify potential risks** or breaking changes
- **Mention alternatives** you considered and why you chose this approach
- **Reference examples** from the codebase or other projects that inspired your solution
- Ask the user: "Does this approach make sense?" or "Should I proceed?"

### 4. Implement Thoughtfully

- Follow the plan you presented
- Stay consistent with the patterns you identified
- Flag any deviations from the plan as you encounter them

### 5. Verify and Test

- Run the full CI check: `yarn lint && yarn build && yarn test`
- Verify your changes work as expected
- Confirm tests pass and coverage is maintained

## Example Workflow

**User Request:** "Add validation for email addresses in user registration"

**Your Response:**

```
I'll first explore how validation is currently handled in the codebase...

[After exploring]
I found that validation is handled using Zod schemas in `src/schemas/`. The user registration logic is in `src/services/user.service.ts`.

Looking at similar patterns, I see projects like tRPC and Remix use Zod for runtime validation with TypeScript inference. The NestJS codebase uses class-validator but Zod seems to be the standard here.

Here's my plan:
1. Add email validation to the existing user schema in `src/schemas/user.schema.ts`
2. Update the registration service in `src/services/user.service.ts` to use this validation
3. Add unit tests in `src/services/user.service.test.ts` to verify email validation
4. Files to modify: user.schema.ts, user.service.ts, user.service.test.ts

The approach will match the existing pattern used for username validation. I'll use Zod's `.email()` validator which is consistent with how other fields are validated.

Does this approach make sense?
```

## Development Workflow

### Before Committing

- Run `yarn lint` to check code quality
- Run `yarn build` to ensure compilation succeeds
- Run `yarn test` to verify all tests pass
- Full CI check: `yarn lint && yarn build && yarn test`

### Branching Strategy

- Create pull requests from the `development` branch
- Never commit directly to `master`

## Code Standards

### TypeScript Best Practices

- Use strict TypeScript configuration - no `any` types unless absolutely necessary
- Prefer `interface` over `type` for object shapes
- Use proper type annotations for function parameters and return types
- Leverage TypeScript's utility types (Partial, Pick, Omit, etc.)
- Use enums or const objects for fixed sets of values

### Code Style

- Use meaningful, descriptive variable and function names
- Prefer `const` over `let`, avoid `var`
- Use arrow functions for callbacks and short functions
- Use async/await over raw Promises
- Keep functions small and focused (single responsibility)
- Extract magic numbers and strings into named constants

### Architecture Patterns

- Follow dependency injection patterns where appropriate
- Maintain separation of concerns
- Keep domain logic pure and testable
- Avoid tight coupling between modules
- Use existing patterns and structures before introducing new ones

### Error Handling

- Use try/catch blocks for async operations
- Throw specific error types, not generic errors
- Provide meaningful error messages
- Handle errors at appropriate levels

### Testing

- Write unit tests for all new functionality
- Aim for high test coverage on business logic
- Use descriptive test names that explain what is being tested
- Follow AAA pattern: Arrange, Act, Assert
- Mock external dependencies appropriately

### Documentation

- Document all public APIs with JSDoc comments
- Explain complex logic with inline comments
- Keep comments up-to-date with code changes
- Document "why" not just "what" for non-obvious code

## Repository Structure

- `src/`: All source code organized by feature/domain

## Key Principles

1. **Research first, code second**: Understand the problem space and existing solutions
2. **Prioritize existing code**: Reuse and refactor existing code before writing new implementations
3. **Consistency**: Match the existing code style and patterns in the file you're modifying
4. **Simplicity**: Write simple, readable code over clever solutions
5. **Type safety**: Leverage TypeScript's type system to catch errors at compile time
6. **Testability**: Write code that is easy to test in isolation
7. **Plan before implementing**: Always present an approach before writing code
8. **Learn from the best**: Look to well-maintained OSS projects for inspiration

## What NOT to Do

- Don't start coding without understanding existing patterns
- Don't use `any` type without strong justification
- Don't ignore TypeScript errors or use `@ts-ignore` without explanation
- Don't commit commented-out code
- Don't skip writing tests for new features
- Don't introduce new dependencies without discussion
- Don't break existing APIs without version consideration
- Don't copy-paste code - extract shared logic instead
- Don't implement without presenting a plan first

## When Making Changes

1. **Explore** the codebase to understand context
2. **Research** best practices and existing solutions
3. **Plan** your approach and present it
4. **Implement** following the plan
5. **Test** thoroughly with existing test patterns
6. **Verify** with `yarn lint && yarn build && yarn test`
7. **Document** any non-obvious decisions

## Questions to Ask Yourself

- Have I explored how this is currently done in the codebase?
- What do leading TypeScript projects do in similar situations?
- Does this follow existing patterns in the codebase?
- Have I presented my plan before implementing?
- Is this the simplest solution that works?
- Have I written/updated tests?
- Is this code self-documenting or does it need comments?
- Will this break any existing functionality?
- Can this be broken into smaller, focused changes?

## Useful Open-Source References

When researching patterns, consider these well-maintained projects:

- **Architecture**: NestJS, tRPC, Remix
- **Database**: Prisma, TypeORM, Drizzle
- **Validation**: Zod, Yup, io-ts
- **Testing**: Vitest, Jest
- **API Design**: Apollo Server, Express.js, Fastify
- **Utilities**: Lodash, Ramda, date-fns
