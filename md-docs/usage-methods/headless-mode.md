# Headless Mode

You can run OpenHands with a single command, without starting the web application. This makes it easy to write scripts and automate tasks with OpenHands. This is different from [CLI Mode](cli-mode.md), which is interactive and better for active development.

## With Python

To run OpenHands in headless mode with Python:

1. Follow the [Development setup instructions](https://github.com/All-Hands-AI/OpenHands/blob/main/Development.md)

2. Run the command:
   ```bash
   poetry run python -m openhands.core.main -t "write a bash script that prints hi" --no-auto-continue
   ```

**Note**: You'll need to set your model, API key, and other settings via environment variables [or the `config.toml` file](https://github.com/All-Hands-AI/OpenHands/blob/main/config.template.toml).

## With Docker

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
       -e LOG_ALL_EVENTS=true \
       -v $WORKSPACE_BASE:/opt/workspace_base \
       -v /var/run/docker.sock:/var/run/docker.sock \
       --add-host host.docker.internal:host-gateway \
       --name openhands-app-$(date +%Y%m%d%H%M%S) \
       docker.all-hands.dev/all-hands-ai/openhands:0.17 \
       python -m openhands.core.main -t "write a bash script that prints hi" --no-auto-continue
   ```

## Use Cases

1. **Automation Scripts**
   - Batch processing tasks
   - Automated code modifications
   - Scheduled maintenance tasks

2. **CI/CD Integration**
   - Code quality checks
   - Automated testing
   - Documentation generation

3. **Batch Operations**
   - Multiple file processing
   - Code refactoring across projects
   - Bulk updates

## Command Line Arguments

- `-t, --task`: The task to perform (required)
- `--no-auto-continue`: Prevent automatic continuation of tasks
- Additional arguments can be found in the help output (`-h, --help`)

## Environment Variables

Important environment variables for headless mode:
- `LLM_MODEL`: The AI model to use
- `LLM_API_KEY`: Your API key
- `WORKSPACE_BASE`: The directory to work in
- `LOG_ALL_EVENTS`: Enable detailed logging

## Best Practices

1. **Task Definition**
   - Be specific and clear in task descriptions
   - Include all necessary context
   - Follow [prompting best practices](../prompting/best-practices.md)

2. **Error Handling**
   - Include proper error handling in scripts
   - Monitor logs for issues
   - Set up appropriate alerting

3. **Resource Management**
   - Clean up containers after use
   - Monitor resource usage
   - Set appropriate timeouts

## Next Steps

- Learn about [GitHub Actions](github-action.md) integration
- Explore [CLI Mode](cli-mode.md) for interactive usage
- Review [GUI Mode](gui-mode.md) for visual interaction