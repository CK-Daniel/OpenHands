# Prompting Best Practices

When working with OpenHands AI software developer, it's crucial to provide clear and effective prompts. This guide outlines best practices for creating prompts that will yield the most accurate and useful responses.

## Characteristics of Good Prompts

Good prompts should be:

1. **Concrete**
   - Explain exactly what functionality should be added
   - Specify what error needs to be fixed
   - Define clear expectations for the outcome

2. **Location-specific**
   - Include relevant file paths
   - Mention specific line numbers when applicable
   - Reference related components or modules

3. **Appropriately scoped**
   - Keep to the size of a single feature
   - Typically not exceeding 100 lines of code
   - Focus on one change at a time

## Examples

### Good Prompt Examples

1. ```
   Add a function `calculate_average` in `utils/math_operations.py` that takes a list of numbers as input and returns their average.
   ```
   - Specific function name
   - Clear file location
   - Well-defined input and output

2. ```
   Fix the TypeError in `frontend/src/components/UserProfile.tsx` occurring on line 42. The error suggests we're trying to access a property of undefined.
   ```
   - Specific error type
   - Exact file and line location
   - Context about the error

3. ```
   Implement input validation for the email field in the registration form. Update `frontend/src/components/RegistrationForm.tsx` to check if the email is in a valid format before submission.
   ```
   - Clear feature request
   - Specific component
   - Defined validation requirement

### Bad Prompt Examples

1. ```
   Make the code better.
   ```
   - Too vague
   - No specific goals
   - No location information

2. ```
   Rewrite the entire backend to use a different framework.
   ```
   - Too broad in scope
   - Lacks specific requirements
   - Not manageable as a single task

3. ```
   There's a bug somewhere in the user authentication. Can you find and fix it?
   ```
   - Lacks specific location
   - No error details
   - Too broad in scope

## Tips for Effective Prompting

1. **Be Specific**
   - State desired outcomes clearly
   - Define success criteria
   - Specify any constraints

2. **Provide Context**
   - Include file paths
   - Reference line numbers
   - Share error messages or logs

3. **Break Down Tasks**
   - Split large tasks into smaller prompts
   - Focus on one change at a time
   - Build features incrementally

4. **Include Error Information**
   - Share complete error messages
   - Include stack traces when available
   - Describe steps to reproduce

5. **Specify Technology Stack**
   - Mention programming languages
   - Reference frameworks used
   - Include version information

## Remember

The more precise and informative your prompt is, the better the AI can assist you in developing or modifying the OpenHands software. Take time to craft your prompts carefully, and don't hesitate to break down complex tasks into smaller, more manageable requests.

## Next Steps

- Explore [Customization](customization.md) options for tailoring OpenHands to your needs
- Learn about specialized [Microagents](microagents.md) for specific tasks
- Review the [Getting Started](../getting-started/README.md) guide for more examples