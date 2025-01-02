# OpenHands WordPress Extension Development Guide

This guide provides detailed instructions for developing the WordPress extension for OpenHands, considering its architecture and runtime environment.

## Architecture Integration

### 1. Runtime Integration

The WordPress extension must integrate with OpenHands' EventStream Runtime system:

```
WordPress Extension
├── Runtime Container
│   ├── WordPress Core
│   ├── Database (MariaDB)
│   ├── Web Server (Apache/Nginx)
│   └── Development Tools
└── OpenHands Integration
    ├── Action Executor
    ├── Event Stream Client
    └── WordPress-specific Plugins
```

#### Key Considerations

1. **Sandboxed Environment**
   - WordPress must run entirely within OpenHands' sandboxed Docker environment
   - All operations must be isolated from the host system
   - Resource usage must be controlled and monitored

2. **Image Building**
   - Follow OpenHands' three-tag system:
     - Source Tag: For WordPress-specific source code
     - Lock Tag: For dependencies and base image
     - Versioned Tag: For version tracking

3. **Plugin System Integration**
   - Create WordPress-specific plugins for OpenHands runtime
   - Implement proper plugin registration and initialization
   - Handle WordPress-specific actions and observations

### 2. Backend Integration

Extend OpenHands' backend to support WordPress operations:

```python
class WordPressAgent(CodeActAgent):
    sandbox_plugins = [
        PluginRequirement("wordpress"),
        PluginRequirement("database"),
        PluginRequirement("web_server")
    ]
```

## Implementation Guidelines

### 1. Plugin Development

Create a WordPress runtime plugin:

```python
from openhands.runtime.plugins import Plugin

class WordPressPlugin(Plugin):
    """WordPress runtime plugin for OpenHands"""
    
    async def initialize(self):
        # Initialize WordPress environment
        pass
        
    async def execute_action(self, action):
        # Handle WordPress-specific actions
        pass
```

### 2. Action Types

Define WordPress-specific actions:

1. **Core Management**
   ```python
   class WordPressCoreAction:
       """WordPress core management actions"""
       install = "wp_install"
       update = "wp_update"
       configure = "wp_configure"
   ```

2. **Development Actions**
   ```python
   class WordPressDevAction:
       """WordPress development actions"""
       create_theme = "wp_create_theme"
       create_plugin = "wp_create_plugin"
       test = "wp_test"
   ```

### 3. Docker Configuration

Create WordPress-specific Docker configuration:

```dockerfile
# Base from OpenHands runtime
FROM ${OPENHANDS_RUNTIME_IMAGE}

# Add WordPress dependencies
RUN apt-get update && apt-get install -y \
    php \
    php-mysql \
    mariadb-client

# WordPress CLI
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
    && chmod +x wp-cli.phar \
    && mv wp-cli.phar /usr/local/bin/wp
```

## Development Process

1. **Setup Development Environment**
   ```bash
   # Create development structure
   mkdir -p wordpress-extension/{runtime,plugins,tools}
   
   # Initialize development environment
   poetry new wordpress-extension
   ```

2. **Implement Core Components**
   - WordPress runtime plugin
   - Action handlers
   - Event stream integration
   - Docker configuration

3. **Testing Strategy**
   ```python
   class TestWordPressExtension:
       """Test WordPress extension functionality"""
       
       async def test_wordpress_installation(self):
           # Test WordPress installation
           pass
           
       async def test_theme_development(self):
           # Test theme development
           pass
   ```

## Best Practices

1. **Runtime Safety**
   - Always use sandboxed operations
   - Validate all inputs
   - Handle permissions carefully
   - Implement proper error handling

2. **Performance**
   - Optimize Docker image size
   - Cache frequently used operations
   - Minimize network operations
   - Use efficient database queries

3. **Security**
   - Follow WordPress security best practices
   - Implement proper authentication
   - Sanitize all inputs
   - Use prepared statements

4. **Code Quality**
   - Follow OpenHands coding standards
   - Write comprehensive tests
   - Document all components
   - Use type hints

## Directory Structure

```
wordpress-extension/
├── runtime/
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── scripts/
├── plugins/
│   ├── wordpress.py
│   └── tests/
├── tools/
│   ├── wp_cli.py
│   └── wp_dev.py
└── tests/
    ├── integration/
    └── unit/
```

## Implementation Phases

1. **Phase 1: Core Setup**
   - Basic WordPress container
   - Runtime plugin structure
   - WP-CLI integration
   - Basic operations

2. **Phase 2: Development Tools**
   - Theme development
   - Plugin development
   - Testing framework
   - Development utilities

3. **Phase 3: Advanced Features**
   - Multisite support
   - Performance optimization
   - Security features
   - Advanced development tools

4. **Phase 4: Integration**
   - OpenHands UI integration
   - Documentation
   - Examples
   - Testing and validation

## Tips for Developers

1. **Understanding OpenHands Architecture**
   - Study the EventStream Runtime system
   - Understand the plugin system
   - Review existing plugins
   - Follow the tagging system

2. **WordPress Integration**
   - Use WP-CLI for operations
   - Follow WordPress coding standards
   - Implement proper error handling
   - Consider multisite support

3. **Testing**
   - Write unit tests
   - Implement integration tests
   - Test in isolated environments
   - Validate WordPress operations

4. **Documentation**
   - Document all functions
   - Provide usage examples
   - Include setup instructions
   - Maintain changelog

## Resources

1. **OpenHands Documentation**
   - [Runtime Architecture](https://docs.all-hands.dev/modules/usage/architecture/runtime)
   - [Backend Architecture](https://docs.all-hands.dev/modules/usage/architecture/backend)
   - [Plugin System](https://github.com/All-Hands-AI/OpenHands/tree/main/openhands/runtime/plugins)

2. **WordPress Development**
   - [WordPress Coding Standards](https://developer.wordpress.org/coding-standards/)
   - [WP-CLI Documentation](https://developer.wordpress.org/cli/commands/)
   - [Theme Development](https://developer.wordpress.org/themes/)
   - [Plugin Development](https://developer.wordpress.org/plugins/)

This guide provides a foundation for developing the WordPress extension while maintaining compatibility with OpenHands' architecture and best practices.