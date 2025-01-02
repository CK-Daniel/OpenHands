# Bug Fixing with OpenHands

OpenHands can help track down and fix bugs in your code. This guide explains how to effectively use OpenHands for debugging and fixing issues in your codebase.

## Effective Bug Fixing Strategies

### 1. Providing Context
When reporting bugs to OpenHands, provide clear context:
```
Currently the email field in the `/subscribe` endpoint is rejecting .io domains. Please fix this.
```

### 2. Case Sensitivity Issues
Handle common issues like case sensitivity:
```
The `search_widgets` function in ./app.py is doing a case-sensitive search. Please make it case-insensitive.
```

### 3. Test-Driven Bug Fixing
Use a test-driven approach:
```
The `hello` function crashes on the empty string. Please write a test that reproduces this bug, then fix the code so it passes.
```

## Best Practices

1. **Diagnosis First**
   - Clearly identify the bug
   - Provide steps to reproduce
   - Share relevant error messages
   - Include affected code sections

2. **Test-Driven Development**
   - Write tests that reproduce the bug
   - Fix the code to pass the tests
   - Add regression tests
   - Verify fixes don't introduce new issues

3. **Documentation**
   - Document the fix
   - Update related documentation
   - Add comments explaining complex fixes
   - Document any workarounds

## Common Bug Types

1. **Logic Errors**
   - Incorrect calculations
   - Wrong conditions
   - Off-by-one errors
   - Edge cases

2. **Input Validation**
   - Missing validation
   - Incorrect validation rules
   - Edge case handling
   - Type conversion issues

3. **Integration Issues**
   - API mismatches
   - Dependency conflicts
   - Configuration problems
   - Environment-specific bugs

4. **Performance Issues**
   - Memory leaks
   - Slow queries
   - Resource contention
   - Scaling problems

## Debugging Process

1. **Reproduce the Bug**
   - Create a minimal test case
   - Document steps to reproduce
   - Identify patterns or triggers

2. **Analyze the Problem**
   - Review error messages
   - Check logs
   - Examine stack traces
   - Use debugging tools

3. **Fix and Verify**
   - Implement the fix
   - Run tests
   - Verify in different environments
   - Check for side effects

## Tips for Success

1. **Be Specific**
   - Provide exact error messages
   - Share relevant code snippets
   - Specify environment details
   - Include version information

2. **Iterative Approach**
   - Start with simple fixes
   - Test thoroughly
   - Refine as needed
   - Document changes

3. **Version Control**
   - Create bug fix branches
   - Write clear commit messages
   - Reference issue numbers
   - Keep changes focused

## Next Steps

After learning about bug fixing, explore our [Best Practices](best-practices.md) guide for more tips on working effectively with OpenHands.