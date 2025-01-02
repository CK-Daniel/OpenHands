# Customizing Agent Behavior

OpenHands can be tailored to work more effectively with specific repositories through repository-specific context and guidelines. This guide explains how to optimize OpenHands for your project.

## Repository Configuration

### The .openhands Directory

Create a `.openhands` directory in your repository's root with the following structure:
```
.openhands/
└── microagents/
    └── repo.md
```

The `repo.md` file contains instructions that will be given to the agent every time it works with your repository.

### Essential Information

Your `repo.md` should include:

1. **Repository Overview**
   - Project purpose
   - Architecture description
   - Key technologies used

2. **Directory Structure**
   - Main directories
   - Purpose of each directory
   - Important files

3. **Development Guidelines**
   - Coding standards
   - Best practices
   - Style guides

4. **Testing Requirements**
   - Test frameworks
   - Testing procedures
   - Coverage requirements

5. **Setup Instructions**
   - Build steps
   - Development environment setup
   - Required dependencies

## Example Configuration

Here's an example `repo.md` file:

```markdown
Repository: MyProject
Description: A web application for task management

Directory Structure:
- src/: Main application code
- tests/: Test files
- docs/: Documentation

Setup:
- Run `npm install` to install dependencies
- Use `npm run dev` for development
- Run `npm test` for testing

Guidelines:
- Follow ESLint configuration
- Write tests for all new features
- Use TypeScript for new code
```

## Customizing Prompts

When working with a customized repository, your prompts should:

1. **Reference Project Standards**
   ```
   Please follow our TypeScript conventions when adding this feature...
   ```

2. **Include Context**
   ```
   Reference the existing implementation in src/components/similar-feature/...
   ```

3. **Specify Testing Requirements**
   ```
   Include unit tests following our Jest testing patterns in tests/components/...
   ```

### Example Customized Prompt
```
Add a new task completion feature to src/components/TaskList.tsx following our existing component patterns.
Include unit tests in tests/components/ and update the documentation in docs/features/.
The component should use our shared styling from src/styles/components.
```

## Best Practices

### 1. Keep Instructions Updated
- Regularly review and update `.openhands` content
- Reflect changes in project structure or standards
- Update dependencies and setup instructions

### 2. Be Specific
- Include exact file paths
- Reference specific patterns
- Detail unique project requirements

### 3. Document Dependencies
- List all required tools
- Specify version requirements
- Include setup instructions

### 4. Include Examples
- Provide sample code snippets
- Show correct implementation patterns
- Demonstrate best practices

### 5. Specify Conventions
- Document naming conventions
- Explain file organization
- Detail code style preferences

## Other Microagents

The `.openhands/microagents/` directory can contain additional instruction files triggered by specific keywords:

- `test.md` for testing-related tasks
- `frontend.md` for frontend development
- `migration.md` for database migrations
- And more...

See [Microagents](microagents.md) for detailed information about creating and using specialized agents.

## Next Steps

- Learn about [Microagents](microagents.md) for specialized task handling
- Review [Best Practices](best-practices.md) for effective prompting
- Check the [Installation Guide](../installation/README.md) for setup details