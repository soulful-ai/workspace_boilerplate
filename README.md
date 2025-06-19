# Workspace Boilerplate

A comprehensive template for creating AI orchestration workspaces using the director-actor pattern. This boilerplate provides the foundation for building complex AI systems with Claude, featuring proper task delegation, quality control, and deployment management.

## Overview

This workspace template implements a flat git submodule architecture where:
- **Director**: Orchestrates and delegates tasks to specialized actors
- **Actors**: Domain-specific AI instances that handle specialized tasks
- **Workspace**: Coordinates all components with shared communication

## Features

- 🎯 **Director-Actor Pattern**: Clear separation of orchestration and implementation
- 🔧 **MCP Protocol Support**: Built-in Model Context Protocol for Claude integration
- 📁 **Flat Architecture**: All components as git submodule siblings
- 🔄 **Shared Communication**: File-based inter-process communication
- 🚀 **Production Ready**: Includes CI/CD patterns and deployment guides
- 🔒 **Security First**: Proper credential and access management

## Quick Start

### 1. Create Your Workspace

```bash
# Clone this template
git clone https://github.com/soulful-ai/workspace_boilerplate my-workspace
cd my-workspace

# Initialize submodules (includes boilerplate templates)
git submodule update --init --recursive

# Remove template git history
rm -rf .git
git init
```

### 2. Set Up Director

```bash
# Copy director boilerplate
cp -r director_boilerplate my-director
cd my-director

# Initialize as your repository
rm -rf .git
git init
git add .
git commit -m "Initial commit"

# Create and push to GitHub
gh repo create [your-org]/my-director --private
git push -u origin main

# Add as workspace submodule
cd ..
rm -rf director_boilerplate  # Remove template
git submodule add https://github.com/[your-org]/my-director director
```

### 3. Add Actors

```bash
# Copy actor boilerplate
cp -r actor_boilerplate my-first-actor
cd my-first-actor

# Customize for your domain
# Edit CLAUDE.md, package.json, etc.

# Initialize and push
rm -rf .git
git init
git add .
git commit -m "Initial commit"
gh repo create [your-org]/my-first-actor --private
git push -u origin main

# Add to workspace
cd ..
git submodule add https://github.com/[your-org]/my-first-actor my-first-actor
```

### 4. Configure and Run

```bash
# Set up director
cd director
./scripts/setup-environment.sh
cp .env.example .env
# Edit .env with your configuration
./scripts/generate-mcp-config.sh

# Start orchestration
npx nx run director:start-orchestration
```

## Architecture

```
my-workspace/
├── CLAUDE.md                  # Workspace instructions for Claude
├── .mcp.json                  # Generated MCP config (gitignored)
├── director/                  # Orchestrator (git submodule)
│   ├── apps/mcp/cli_use/     # Director MCP server
│   ├── prompts/              # Orchestration guides
│   └── scripts/              # Automation tools
├── actor1/                    # Domain actor (git submodule)
├── actor2/                    # Another actor (git submodule)
└── .shared-workspace/         # Inter-process communication
```

## Component Templates

### Director Boilerplate
- Full Nx monorepo setup
- MCP server implementation
- Actor management scripts
- Orchestration patterns
- [View Template](director_boilerplate/README.md)

### Actor Boilerplate
- Domain-specific structure
- MCP server integration
- Task processing patterns
- Testing framework
- [View Template](actor_boilerplate/README.md)

## Key Concepts

### Communication Flow
1. User interacts with Director via Claude
2. Director analyzes and delegates to Actors
3. Actors process tasks and report progress
4. Director ensures quality and coordinates results

### Port Convention
- Director: 9000
- Actor 1: 9001
- Actor 2: 9002
- Additional actors: 900X

### Best Practices
- One repository per component
- Flat submodule structure
- Clear domain boundaries
- Immediate challenge escalation
- Test environment focus

## Customization Guide

### 1. Director Customization
- Define your orchestration logic
- Set up quality standards
- Configure actor management
- Implement user interaction patterns

### 2. Actor Specialization
- Choose domain expertise
- Implement specialized tools
- Define communication patterns
- Create test deployment logic

### 3. Workspace Configuration
- Update CLAUDE.md with your specifics
- Configure environment variables
- Set up CI/CD pipelines
- Implement monitoring

## Security

- Store credentials in `.env` files (never commit)
- Use environment variables for sensitive data
- Configure MCP access controls
- Implement proper authentication

## Contributing

This is a template repository. To contribute:
1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

MIT License - see [LICENSE](LICENSE) file

## Resources

- [Director Boilerplate Docs](director_boilerplate/README.md)
- [Actor Boilerplate Docs](actor_boilerplate/README.md)
- [MCP Protocol Specification](https://modelcontextprotocol.io/)
- [Nx Documentation](https://nx.dev/)

## Support

For issues or questions:
- Check component documentation
- Review example implementations
- Open an issue on GitHub
- Use web search for latest practices

---

Built with ❤️ for AI orchestration at scale