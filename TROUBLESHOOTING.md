# Troubleshooting Guide

This document records issues encountered during development and their solutions.

## Type Consolidation Issues

### ESLint TypeScript Version Compatibility Issue

#### Problem
During the type consolidation work, we encountered ESLint errors related to TypeScript version compatibility. The errors appeared when running ESLint on the consolidated type files:

```
Error: Error while loading rule '@typescript-eslint/no-unused-vars': You have used a rule which requires parserServices to be generated. You must therefore provide a value for the "parserOptions.project" property for @typescript-eslint/parser.
```

#### Root Cause
The ESLint configuration was not properly set up to work with TypeScript 5.7.3. The `parserOptions.project` property was missing in the ESLint configuration, which is required for certain TypeScript-specific rules.

#### Solution
A temporary workaround was to disable the problematic ESLint rules in the files where they were causing issues. However, a proper solution would be to update the ESLint configuration to include:

```js
// In eslint.config.mjs
parserOptions: {
  project: './tsconfig.json',
  tsconfigRootDir: __dirname,
},
```

This will be addressed in a separate task.

#### Lessons Learned
- Always check ESLint configuration when upgrading TypeScript versions
- Make sure `parserOptions.project` is set correctly for TypeScript-specific rules
- Consider using ESLint's `--fix` option to automatically fix simple issues

### Duplicate Type Definitions

#### Problem
We found multiple definitions of the same types across different files, leading to compatibility issues when components interacted with each other.

#### Root Cause
As the application grew, different developers created similar but slightly different type definitions in different files, rather than reusing existing types.

#### Solution
1. Consolidated all indicator types to `types/indicators.ts`
2. Consolidated Strategy interfaces to `types/strategy.ts`
3. Moved optimization types to `types/optimization.ts`
4. Created adapter functions in `typeConversions.ts` to handle conversion between similar types

#### Lessons Learned
- Maintain a centralized location for type definitions
- Document type hierarchies and relationships
- Use import statements to reuse types instead of redefining them

## Skipped Tests in strategyStore.test.ts

### Problem
Several tests in `strategyStore.test.ts` are currently skipped (using `it.skip`), which reduces test coverage.

### Root Cause
The tests were likely skipped due to changes in the API or type definitions that broke the tests.

### Solution
These tests need to be updated to work with the consolidated types. This will be addressed in a separate task.

### Lessons Learned
- Update tests when making significant changes to type definitions
- Don't leave tests skipped for extended periods
- Consider using TypeScript's strict mode to catch type issues earlier

## Large Files Exceeding GitHub's Size Limits

### Problem
When attempting to push changes to GitHub, we encountered errors due to large files exceeding GitHub's file size limits:

```
remote: error: File venv/lib/python3.12/site-packages/playwright/driver/node is 114.52 MB; this exceeds GitHub's file size limit of 100.00 MB
remote: error: File terraform/envs/staging/.terraform/providers/registry.terraform.io/hashicorp/aws/5.84.0/linux_amd64/terraform-provider-aws_v5.84.0_x5 is 629.55 MB; this exceeds GitHub's file size limit of 100.00 MB
```

### Root Cause
The repository contained large binary files that should not be tracked by Git.

### Solution
1. Updated `.gitignore` to exclude large files and directories
2. Created a clean branch with only the necessary files
3. Used Git LFS for large files that need to be tracked

### Lessons Learned
- Always check file sizes before committing
- Use `.gitignore` to exclude large binary files
- Consider using Git LFS for large files that need to be tracked
- Create clean branches when dealing with large file issues 