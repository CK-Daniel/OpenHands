# Refactoring Code with OpenHands

OpenHands excels at refactoring existing code, especially when working with smaller, focused changes. This guide shows you how to effectively use OpenHands for code refactoring tasks.

## Common Refactoring Tasks

### Variable Renaming
Improve code readability by renaming variables:
```
Please rename all the single-letter variables in ./app.go
```

### Function Splitting
Break down large functions into smaller, more manageable pieces:
```
Please break the function `build_and_deploy_widgets` into two functions, `build_widgets` and `deploy_widgets` in widget.php
```

### File Organization
Restructure files for better organization:
```
Please break ./api/routes.js into separate files for each route
```

## Best Practices for Refactoring

1. **Small, Focused Changes**
   - Work on one type of refactoring at a time
   - Keep changes isolated and specific
   - Test after each refactoring step

2. **Maintain Functionality**
   - Ensure behavior remains unchanged
   - Run existing tests after refactoring
   - Add new tests if needed

3. **Version Control**
   - Commit frequently
   - Use descriptive commit messages
   - Create separate branches for refactoring

4. **Documentation**
   - Update documentation to reflect changes
   - Document complex refactoring decisions
   - Keep comments up to date

## Types of Refactoring

1. **Code Structure**
   - Breaking down large functions
   - Extracting common logic
   - Moving code to appropriate modules

2. **Naming and Readability**
   - Renaming variables and functions
   - Improving formatting
   - Adding meaningful comments

3. **Architecture**
   - Reorganizing file structure
   - Implementing design patterns
   - Improving module organization

4. **Performance**
   - Optimizing algorithms
   - Reducing complexity
   - Improving resource usage

## Tips for Success

1. **Provide Context**
   - Share relevant code snippets
   - Explain the goal of the refactoring
   - Mention any constraints or requirements

2. **Iterative Approach**
   - Start with simple refactoring
   - Review and test changes
   - Gradually tackle more complex refactoring

3. **Testing Strategy**
   - Run existing tests
   - Add new tests when needed
   - Verify edge cases

## Next Steps

After mastering refactoring, learn how to use OpenHands for [Bug Fixing](bug-fixing.md) to improve code quality further.