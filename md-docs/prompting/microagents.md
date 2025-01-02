# Micro-Agents

OpenHands uses specialized micro-agents to handle specific tasks and contexts efficiently. These are small, focused components that provide specialized behavior and knowledge for particular scenarios.

## Overview

Micro-agents are defined in markdown files under the `openhands/agenthub/codeact_agent/micro/` directory. Each micro-agent has:

- A unique name
- The agent type (typically CodeActAgent)
- Trigger keywords that activate the agent
- Specific instructions and capabilities

## Available Micro-Agents

### GitHub Agent

**File**: `github.md`  
**Triggers**: `github`, `git`

The GitHub agent specializes in GitHub API interactions and repository management:

- Has access to a `GITHUB_TOKEN` for API authentication
- Follows strict guidelines for repository interactions
- Handles branch management and pull requests
- Uses the GitHub API instead of web browser interactions

Key features:
- Branch protection (prevents direct pushes to main/master)
- Automated PR creation
- Git configuration management
- API-first approach for GitHub operations

### NPM Agent

**File**: `npm.md`  
**Triggers**: `npm`

Specializes in handling npm package management with focus on:
- Non-interactive shell operations
- Automated confirmation handling using Unix 'yes' command
- Package installation automation

### Custom Micro-Agents

Create your own micro-agents by adding new markdown files to the micro-agents directory:

```markdown
---
name: agent_name
agent: CodeActAgent
triggers:
- trigger_word1
- trigger_word2
---

Instructions and capabilities for the micro-agent...
```

## Best Practices

When working with micro-agents:

1. **Use Appropriate Triggers**
   - Include relevant trigger words
   - Be specific about the agent you need

2. **Follow Agent Guidelines**
   - Respect agent-specific instructions
   - Work within defined limitations

3. **API-First Approach**
   - Prefer API endpoints over web interfaces
   - Use authenticated requests when available

4. **Automation Friendly**
   - Design for non-interactive environments
   - Handle automated workflows efficiently

## Integration

Micro-agents are automatically integrated into OpenHands' workflow:
- Monitor incoming commands for trigger words
- Activate when relevant triggers are detected
- Apply specialized knowledge and capabilities
- Follow specific guidelines and restrictions

## Example Usage

```bash
# GitHub agent example
git checkout -b feature-branch
git commit -m "Add new feature"
git push origin feature-branch

# NPM agent example
yes | npm install package-name
```

## Contributing a Micro-Agent

### 1. Planning Your Micro-Agent

Consider:
- Specific problem or use case to address
- Unique capabilities or knowledge needed
- Appropriate trigger words
- Necessary constraints or guidelines

### 2. File Structure

Create a new markdown file in `openhands/agenthub/codeact_agent/micro/` with a descriptive name.

### 3. Required Components

#### Front Matter
```yaml
---
name: your_agent_name
agent: CodeActAgent
triggers:
- trigger_word1
- trigger_word2
---
```

#### Instructions
```markdown
You are responsible for [specific task/domain].

Key responsibilities:
1. [Responsibility 1]
2. [Responsibility 2]

Guidelines:
- [Guideline 1]
- [Guideline 2]

Examples of usage:
[Example 1]
[Example 2]
```

### 4. Best Practices for Development

1. **Clear Scope**
   - Focus on specific domain/task
   - Avoid overlap with existing agents

2. **Explicit Instructions**
   - Clear, unambiguous guidelines
   - Detailed behavior specifications

3. **Useful Examples**
   - Practical use cases
   - Common scenarios

4. **Safety First**
   - Include necessary warnings
   - Document constraints

5. **Integration Awareness**
   - Consider interaction with other components
   - Handle dependencies appropriately

### 5. Testing Your Micro-Agent

Before submission:
1. Test with various prompts
2. Verify trigger word activation
3. Ensure clear instructions
4. Check for conflicts

### 6. Example Implementation

```markdown
---
name: docker
agent: CodeActAgent
triggers:
- docker
- container
---

You are responsible for Docker container management and Dockerfile creation.

Key responsibilities:
1. Create and modify Dockerfiles
2. Manage container lifecycle
3. Handle Docker Compose configurations

Guidelines:
- Always use official base images when possible
- Include necessary security considerations
- Follow Docker best practices for layer optimization

Examples:
1. Creating a Dockerfile:
   FROM node:18-alpine
   WORKDIR /app
   COPY package*.json ./
   RUN npm install
   COPY . .
   CMD ["npm", "start"]

2. Docker Compose usage:
   version: '3'
   services:
     web:
       build: .
       ports:
         - "3000:3000"

Remember to:
- Validate Dockerfile syntax
- Check for security vulnerabilities
- Optimize for build time and image size
```

### 7. Submission Process

1. Create micro-agent file
2. Test thoroughly
3. Submit pull request including:
   - New micro-agent file
   - Updated documentation
   - Description of agent's purpose

## Next Steps

- Review [Best Practices](best-practices.md) for effective prompting
- Learn about [Customization](customization.md) options
- Check the [Installation Guide](../installation/README.md) for setup details