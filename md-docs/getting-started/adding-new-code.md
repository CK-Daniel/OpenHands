# Adding New Code

OpenHands can effectively add new code to existing projects. This guide explains how to integrate new functionality into your codebase.

## Adding New Features

### GitHub Actions
OpenHands can add new workflows and actions to your project. For example:
```
Please add a GitHub action that lints the code in this repository
```
The agent will:
1. Examine your codebase to determine the appropriate linter
2. Create the workflow file in `.github/workflows/`
3. Configure the linting rules

### API Routes
Adding new endpoints to your API:
```
Please modify ./backend/api/routes.js to add a new route that returns a list of all tasks
```

### UI Components
Creating new frontend components:
```
Please add a new React component that displays a list of Widgets to the ./frontend/components directory. It should use the existing Widget component.
```

## Providing Context

### Explicit Context
When adding new code, provide context about:
1. File locations
2. Existing components or functions to use
3. Expected behavior
4. Required dependencies

### Implicit Context
OpenHands can discover context by:
- Using `ls` to explore the directory structure
- Using `grep` to search through files
- Reading related files to understand patterns

## Best Practices

1. **Provide Clear Requirements**
   - Specify exact file locations
   - Define expected behavior
   - Mention any dependencies or existing components to use

2. **Review Changes**
   - Check the added code for consistency
   - Verify integration with existing code
   - Test new functionality

3. **Iterative Development**
   - Start with basic functionality
   - Add features incrementally
   - Test at each step

4. **Documentation**
   - Ask OpenHands to document new code
   - Update existing documentation
   - Add comments for complex logic

## Common Use Cases

1. **Adding New Features**
   - API endpoints
   - UI components
   - Utility functions
   - Database models

2. **Integration**
   - Third-party services
   - APIs
   - Authentication systems
   - Analytics

3. **Configuration**
   - Build scripts
   - CI/CD pipelines
   - Environment configurations
   - Docker configurations

## Next Steps

After learning to add new code, explore how to improve existing code through [Refactoring](refactoring.md).