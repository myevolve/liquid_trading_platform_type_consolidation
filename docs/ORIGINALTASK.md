# Original Task: Type Consolidation

## Task Description

Consolidate type definitions across the frontend codebase to improve maintainability, reduce duplication, and ensure type consistency.

## Requirements

1. Identify all files with duplicate type definitions
2. Create consolidated type files for related types:
   - Indicator-related types
   - Strategy-related interfaces
   - Optimization-related types
3. Create adapter functions for type compatibility if needed
4. Update imports across the codebase
5. Fix type compatibility issues in components
6. Verify that the application runs correctly with the consolidated types
7. Document the changes and any issues encountered

## Background

The frontend codebase has grown organically, leading to duplicate type definitions across different files. This has caused type compatibility issues when components interact with each other. The goal is to organize related types into dedicated files and update imports across the codebase.

## Previous Work

A previous PR fixed type compatibility issues in the ParameterOptimization component, but it was a temporary solution. This task aims to provide a more comprehensive solution by consolidating all type definitions.

## Related Issues

- Type compatibility issues in TradingChart component
- Duplicate type definitions causing confusion
- ESLint configuration issues related to TypeScript version compatibility 