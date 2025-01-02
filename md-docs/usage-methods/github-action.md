# Using the OpenHands GitHub Action

This guide explains how to use the OpenHands GitHub Action, both within the OpenHands repository and in your own projects.

## Using the Action in the OpenHands Repository

To use the OpenHands GitHub Action in a repository:

1. Create an issue in the repository
2. Either:
   - Add the `fix-me` label to the issue, or
   - Leave a comment on the issue starting with `@openhands-agent`

The action will automatically trigger and attempt to resolve the issue.

## Installing the Action in a New Repository

To install the OpenHands GitHub Action in your own repository, follow the [README for the OpenHands Resolver](https://github.com/All-Hands-AI/OpenHands/blob/main/openhands/resolver/README.md).

## Usage Tips

### Iterative Resolution

1. Create an issue in the repository
2. Add the `fix-me` label or comment with `@openhands-agent`
3. Review the resolution attempt in the pull request
4. Provide feedback through:
   - General comments
   - Review comments
   - Inline thread comments
5. Add the `fix-me` label to the pull request, or address specific comments with `@openhands-agent`

### Label versus Macro

Two ways to trigger OpenHands:

1. **Label (`fix-me`)**
   - Requests OpenHands to address the **entire** issue or pull request
   - Use for comprehensive solutions

2. **Macro (`@openhands-agent`)**
   - Considers only the issue/pull request description and **the specific comment**
   - Use for targeted responses

## Advanced Settings

### Custom Repository Settings

You can provide custom directions for OpenHands by following the [README for the resolver](https://github.com/All-Hands-AI/OpenHands/blob/main/openhands/resolver/README.md#providing-custom-instructions).

### Custom Configurations

GitHub resolver supports customization through [repository secrets](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions?tool=webui#creating-secrets-for-a-repository) or [repository variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables#creating-configuration-variables-for-a-repository).

Available configuration options:

| Attribute Name | Type | Purpose | Example |
|---------------|------|----------|----------|
| `LLM_MODEL` | Variable | Set the LLM to use with OpenHands | `LLM_MODEL="anthropic/claude-3-5-sonnet-20241022"` |
| `OPENHANDS_MAX_ITER` | Variable | Set max limit for agent iterations | `OPENHANDS_MAX_ITER=10` |
| `OPENHANDS_MACRO` | Variable | Customize default macro for invoking the resolver | `OPENHANDS_MACRO=@resolveit` |
| `OPENHANDS_BASE_CONTAINER_IMAGE` | Variable | Custom Sandbox ([learn more](https://docs.all-hands.dev/modules/usage/how-to/custom-sandbox-guide)) | `OPENHANDS_BASE_CONTAINER_IMAGE="custom_image"` |

## Best Practices

1. **Issue Creation**
   - Be clear and specific in issue descriptions
   - Include relevant context and requirements
   - Follow [prompting best practices](../prompting/best-practices.md)

2. **Feedback Process**
   - Review changes thoroughly
   - Provide constructive feedback
   - Be specific about needed changes

3. **Configuration Management**
   - Use appropriate variables for your needs
   - Keep secrets secure
   - Document custom configurations

## Example Workflow

```yaml
name: OpenHands Auto-Resolver
on:
  issues:
    types: [opened, labeled]
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]

jobs:
  resolve:
    runs-on: ubuntu-latest
    steps:
      - uses: all-hands-ai/openhands-resolver@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          llm-api-key: ${{ secrets.LLM_API_KEY }}
```

## Next Steps

- Review [GUI Mode](gui-mode.md) for interactive development
- Explore [CLI Mode](cli-mode.md) for command-line usage
- Learn about [Headless Mode](headless-mode.md) for automation