# Starting OpenHands

The easiest way to run OpenHands is using Docker. This guide will walk you through the process.

## Docker Installation

Run the following commands to pull and start OpenHands:

```bash
# Pull the runtime image
docker pull docker.all-hands.dev/all-hands-ai/runtime:0.17-nikolaik

# Run OpenHands
docker run -it --rm --pull=always \
    -e SANDBOX_RUNTIME_CONTAINER_IMAGE=docker.all-hands.dev/all-hands-ai/runtime:0.17-nikolaik \
    -e LOG_ALL_EVENTS=true \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v ~/.openhands-state:/.openhands-state \
    -p 3000:3000 \
    --add-host host.docker.internal:host-gateway \
    --name openhands-app \
    docker.all-hands.dev/all-hands-ai/openhands:0.17
```

## Alternative Running Methods

OpenHands can also be run in several other ways:
- [Headless mode](https://docs.all-hands.dev/modules/usage/how-to/headless-mode) for scriptable operations
- [Interactive CLI](https://docs.all-hands.dev/modules/usage/how-to/cli-mode) for command-line usage
- [GitHub Action](https://docs.all-hands.dev/modules/usage/how-to/github-action) for CI/CD integration

## Verifying Installation

After running the command, OpenHands will be available at [http://localhost:3000](http://localhost:3000).

## Next Steps

Once the application is running, proceed to the [Setup](setup.md) guide to configure your OpenHands installation.