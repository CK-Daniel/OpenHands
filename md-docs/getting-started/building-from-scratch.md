# Building From Scratch

OpenHands excels at "greenfield" tasks - creating new projects from scratch without needing context from existing codebases. This guide will show you how to effectively build new projects with OpenHands.

## Best Practices for New Projects

1. **Start Simple**: Begin with a basic implementation
2. **Be Specific**: Provide clear requirements about:
   - Technology stack
   - Features needed
   - Expected behavior
3. **Iterate Gradually**: Build functionality incrementally
4. **Version Control**: Commit changes frequently

## Example: Building a TODO App

### 1. Initial Setup
Start with a basic prompt:
```
Please build a basic TODO list app in React. It should be frontend-only, and all state should be kept in localStorage.
```

### 2. Adding Features
Once the basic structure is in place, add features incrementally:
```
Please allow adding an optional due date to every task
```

### 3. Version Control
Regularly commit your changes:
```
Please commit the changes and push them to a new branch called "feature/due-dates"
```

## Project Structure Tips

When building from scratch:
1. **Define Architecture First**: Ask OpenHands to outline the project structure before implementing details
2. **Document as You Go**: Request documentation for new features
3. **Include Tests**: Ask for test coverage of new functionality
4. **Follow Standards**: Specify any coding standards or patterns you want to follow

## Example Project Types

OpenHands can help build various types of projects from scratch:

1. **Web Applications**
   - Frontend frameworks (React, Vue, Angular)
   - Backend services (Node.js, Python, Go)
   - Full-stack applications

2. **Command Line Tools**
   - System utilities
   - Development tools
   - Data processing scripts

3. **APIs and Services**
   - REST APIs
   - GraphQL services
   - Microservices

## Next Steps

Once you're comfortable building new projects, learn how to [Add New Code](adding-new-code.md) to existing projects.