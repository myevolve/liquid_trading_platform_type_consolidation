# Project Rules

## Type Definitions

1. **Centralized Type Definitions**: All type definitions should be in dedicated files in the `types` directory.
2. **Type Naming Conventions**: Use PascalCase for interface and type names, and camelCase for properties.
3. **Documentation**: Add JSDoc comments to all type definitions.
4. **No Duplicate Definitions**: Do not redefine types in multiple files. Import them from the central location.
5. **Type Hierarchy**: Document type hierarchies and relationships.

## Code Organization

1. **Component Structure**: Components should be organized by feature or domain.
2. **Utility Functions**: Utility functions should be in the `utils` directory.
3. **Services**: API services should be in the `services` directory.
4. **Constants**: Constants should be in the `constants` directory.

## Testing

1. **Test Coverage**: All components should have corresponding test files.
2. **Test Naming**: Test files should have the same name as the file they are testing, with a `.test.ts` or `.test.tsx` extension.
3. **No Skipped Tests**: Do not leave tests skipped for extended periods. Fix or remove them.
4. **Mock Data**: Use mock data for tests, not real API calls.

## Documentation

1. **README**: Each directory should have a README.md file explaining its purpose.
2. **TROUBLESHOOTING**: Document issues encountered and their solutions in TROUBLESHOOTING.md.
3. **CURRENTTASK**: Keep track of the current task in CURRENTTASK.md.
4. **ORIGINALTASK**: Document the original task in ORIGINALTASK.md.

## Git Workflow

1. **Branch Naming**: Use descriptive branch names with a prefix indicating the type of change (e.g., `feature/`, `fix/`, `refactor/`).
2. **Commit Messages**: Write clear and concise commit messages. Include "[Cursor] " in the commit message.
3. **Pull Requests**: Create a pull request for each feature or fix. Include a description of the changes.
4. **Code Review**: All code should be reviewed before merging.
5. **Large Files**: Do not commit large binary files to the repository. Use Git LFS if necessary.

## ESLint and TypeScript

1. **ESLint Configuration**: Ensure ESLint configuration is compatible with the TypeScript version.
2. **TypeScript Version**: Use TypeScript 5.7.3 or later.
3. **Strict Mode**: Enable TypeScript's strict mode to catch type issues earlier.
4. **No Any**: Avoid using `any` type. Use proper type definitions instead. 