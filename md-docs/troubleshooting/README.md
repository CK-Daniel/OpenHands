# 🚧 Troubleshooting

This guide helps you resolve common issues you might encounter while using OpenHands.

> **Important**: OpenHands only supports Windows via WSL. Please be sure to run all commands inside your WSL terminal.

## Common Issues

### Launch Docker Client Failed

**Description**

When running OpenHands, you might see the following error:
```
Launch docker client failed. Please make sure you have installed docker and started docker desktop/daemon.
```

**Resolution**

Try these steps in order:
1. Confirm `docker` is running on your system
   - Run `docker ps` in the terminal to verify
2. If using Docker Desktop:
   - Enable `Settings > Advanced > Allow the default Docker socket to be used`
   - Enable `Settings > Resources > Network > Enable host networking` if needed
3. If issues persist, try reinstalling Docker Desktop

### Error Building Runtime Docker Image

**Description**

Session start failures with errors like:
```
debian-security bookworm-security
InRelease At least one invalid signature was encountered.
```

This typically occurs when the hash of an existing external library changes and your local docker instance has cached a previous version.

**Resolution**

1. Stop runtime containers:
   ```bash
   docker ps --filter name=openhands-runtime- --filter status=running -aq | xargs docker stop
   ```

2. Remove runtime containers:
   ```bash
   docker rmi $(docker images --filter name=openhands-runtime- -q --no-trunc)
   ```

3. Clean up Docker system:
   ```bash
   docker container prune -f && docker image prune -f
   ```

## Development Workflow Issues

### Environment Setup

1. **Python Environment**
   - Verify Python version compatibility
   - Check virtual environment activation
   - Validate package installations

2. **Docker Configuration**
   - Ensure proper permissions
   - Verify network settings
   - Check resource allocations

3. **WSL (Windows Users)**
   - Confirm WSL installation
   - Verify WSL version
   - Check Docker WSL integration

## Best Practices for Avoiding Issues

1. **Regular Maintenance**
   - Keep Docker images updated
   - Clean up unused containers
   - Monitor disk space

2. **Configuration Management**
   - Back up configuration files
   - Document custom settings
   - Use version control

3. **System Requirements**
   - Monitor resource usage
   - Maintain sufficient disk space
   - Keep dependencies updated

## Getting Help

If you encounter issues not covered in this guide:

1. Check the [GitHub Issues](https://github.com/All-Hands-AI/OpenHands/issues)
2. Join our [Slack Community](https://join.slack.com/t/openhands-ai/shared_invite/zt-2wkh4pklz-w~h_DVDtEe9H5kyQlcNxVw)
3. Visit our [Discord Server](https://discord.gg/ESHStjSjD4)

## Next Steps

- Review the [Installation Guide](../installation/README.md) for proper setup
- Check [Usage Methods](../usage-methods/README.md) for different ways to use OpenHands
- Explore [Best Practices](../getting-started/best-practices.md) to avoid common issues