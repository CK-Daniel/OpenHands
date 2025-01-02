# OpenHands Versions

OpenHands follows semantic versioning (semver) and provides multiple options for version selection based on your stability requirements and feature needs.

## Available Version Tags

### Latest Stable Release
```bash
docker.all-hands.dev/all-hands-ai/openhands:0.17
```
This is the recommended version for most users, providing the latest stable features and bug fixes.

### Specific Versions

You can use specific version tags in the format:
```bash
docker.all-hands.dev/all-hands-ai/openhands:$VERSION
```
Replace `$VERSION` with your desired version number.

### Version Tag Types

1. **Major Version Tags** (e.g., `0`)
   - Points to the latest `0.x.x` release
   - Broadest update scope
   - May include breaking changes

2. **Minor Version Tags** (e.g., `0.9`)
   - Points to the latest `0.9.x` release
   - Includes new features and bug fixes
   - Should be backward compatible

3. **Patch Version Tags** (e.g., `0.9.1`)
   - Most specific version control
   - Contains only bug fixes
   - Safest option for stability

### Development Version

For testing or development purposes, you can use the development version:
```bash
docker.all-hands.dev/all-hands-ai/openhands:main
```
⚠️ **Warning**: This version is unstable and should not be used in production environments.

## Choosing the Right Version

- **Production Use**: Choose a specific patch version for maximum stability
- **Development**: Use the `main` tag for testing new features
- **General Use**: The latest stable release is recommended

## Development Workflow

For information about the development workflow, refer to the [Development Guide](https://github.com/All-Hands-AI/OpenHands/blob/main/Development.md).

## Troubleshooting

If you encounter any issues with versions, please check our [Troubleshooting Guide](https://docs.all-hands.dev/modules/usage/troubleshooting).