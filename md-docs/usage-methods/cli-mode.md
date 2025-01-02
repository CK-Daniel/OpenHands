# CLI Mode

OpenHands can be run in an interactive CLI mode, which allows users to start an interactive session via the command line. This mode is different from the [headless mode](headless-mode.md), which is non-interactive and better for scripting.

## With Python

To start an interactive OpenHands session via the command line:

1. Ensure you have followed the [Development setup instructions](https://github.com/All-Hands-AI/OpenHands/blob/main/Development.md)

2. Run the following command:
   ```bash
   poetry run python -m openhands.core.cli
   ```

This command will start an interactive session where you can input tasks and receive responses from OpenHands.

**Note**: You'll need to set your model, API key, and other settings via environment variables [or the `config.toml` file](https://github.com/All-Hands-AI/OpenHands/blob/main/config.template.toml).

## With Docker

To run OpenHands in CLI mode with Docker:

1. Set `WORKSPACE_BASE` to the directory you want OpenHands to edit:
   ```bash
   WORKSPACE_BASE=$(pwd)/workspace
   ```

2. Set `LLM_MODEL` to the model you want to use:
   ```bash
   LLM_MODEL="anthropic/claude-3-5-sonnet-20241022"
   ```

3. Set `LLM_API_KEY` to your API key:
   ```bash
   LLM_API_KEY="sk_test_12345"
   ```

4. Run the following Docker command:
   ```bash
   docker run -it \
       --pull=always \
       -e SANDBOX_RUNTIME_CONTAINER_IMAGE=docker.all-hands.dev/all-hands-ai/runtime:0.17-nikolaik \
       -e SANDBOX_USER_ID=$(id -u) \
       -e WORKSPACE_MOUNT_PATH=$WORKSPACE_BASE \
       -e LLM_API_KEY=$LLM_API_KEY \
       -e LLM_MODEL=$LLM_MODEL \
       -v $WORKSPACE_BASE:/opt/workspace_base \
       -v /var/run/docker.sock:/var/run/docker.sock \
       --add-host host.docker.internal:host-gateway \
       --name openhands-app-$(date +%Y%m%d%H%M%S) \
       docker.all-hands.dev/all-hands-ai/openhands:0.17 \
       python -m openhands.core.cli
   ```

## Examples of CLI Commands and Expected Outputs

### Example 1: Simple Task
```
How can I help? >> Write a Python script that prints "Hello, World!"

🤖 Sure! Here is a Python script that prints "Hello, World!":

❯ print("Hello, World!")
```

### Example 2: Bash Command
```
How can I help? >> Create a directory named "test_dir"

🤖 Creating a directory named "test_dir":

❯ mkdir test_dir
```

### Example 3: Error Handling
```
How can I help? >> Delete a non-existent file

🤖 An error occurred. Please try again.
```

## Tips for CLI Usage

1. **Environment Setup**
   - Ensure all required environment variables are set
   - Verify workspace permissions
   - Check Docker configuration if using Docker mode

2. **Command Structure**
   - Be clear and specific with commands
   - Follow [prompting best practices](../prompting/best-practices.md)
   - Use proper syntax for complex operations

3. **Error Handling**
   - Pay attention to error messages
   - Check logs for detailed information
   - Verify environment configuration if issues persist

## Next Steps

- Learn about [Headless Mode](headless-mode.md) for automated operations
- Explore [GitHub Actions](github-action.md) integration
- Review [GUI Mode](gui-mode.md) for visual interaction