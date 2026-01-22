# Vibe Code Template

A modern project template for building applications with opencode AI assistance and spec-kit specification tools.

## Quick Start

Download and initialize the template:

```bash
curl -L https://raw.githubusercontent.com/loxoron218/vibe-code-template/refs/heads/main/start.sh -o start.sh && chmod +x start.sh && ./start.sh
```

This script will:
- Clone the template repository
- Move opencode configuration to your home directory
- Initialize a Rust project
- Install and configure spec-kit CLI

## Features

- **opencode Integration**: Pre-configured AI coding assistant with multiple model support
- **spec-kit**: Project specification and planning tools
- **Rust Tooling**: Pre-configured clippy and rustfmt for code quality and formatting
- **Specialized Review Agents**:
  - `performance-review`: Analyzes code for performance bottlenecks and optimization opportunities
  - `security-review`: Identifies security vulnerabilities and best practice violations
  - `uncommitted-review`: General code quality review with focus on maintainability
- **Development Skills**:
  - `gtk-ui-ux-engineer`: GNOME Human Interface Guidelines and libadwaita patterns
  - `performance-optimization`: High-performance coding techniques and patterns
  - `senior-rust-practices`: Modern idiomatic Rust, error handling, and testing
  - `sql-optimization-patterns`: Database query optimization strategies

## Documentation

Additional documentation is available in the `docs/` directory:

- **docs/AGENTS.md**: Detailed descriptions of all available review agents and their capabilities
- **docs/information.md**: General project information and setup details

## Spec-Kit Slash Commands

| Command | Description |
| --- | --- |
| `/speckit.constitution` | Create or update project governing principles and development guidelines. |
| `/speckit.specify` | Define requirements, user stories, and the scope of what you want to build. |
| `/speckit.plan` | Generate technical implementation plans based on your chosen tech stack. |
| `/speckit.tasks` | Break down the plan into a granular, actionable task list. |
| `/speckit.implement` | Automatically execute tasks to build features according to the approved plan. |

## Configuration Files

### opencode Configuration (`.opencode/opencode.json`)
Main configuration file for the opencode AI assistant, defining:
- Model selection and API settings
- Agent and skill activation
- Context limits and behavior preferences

### Rust Tooling

The template includes pre-configured Rust development tools:

- **clippy.toml**: Configures the Rust linter with sensible defaults:
  - Enforces consistent formatting for format arguments
  - Limits excessive nesting to 3 levels
  - Restricts absolute paths to 1 segment

- **rustfmt.toml**: Configures the Rust code formatter:
  - Organizes imports with `One` granularity
  - Uses 2024 style edition
  - Enables unstable features

## Project Structure

```
.
├── .opencode/                            # opencode AI assistant configuration
│   ├── agent/                            # Specialized review agents
│   │   ├── performance-review.md         # Performance-focused code review
│   │   ├── security-review.md            # Security-focused code review
│   │   └── uncommitted-review.md         # General code quality review
│   ├── skills/                           # Development skills and patterns
│   │   ├── gtk-ui-ux-engineer.md         # GTK/libadwaita UI/UX best practices
│   │   ├── performance-optimization.md   # Performance optimization techniques
│   │   ├── senior-rust-practices.md      # Modern Rust patterns and practices
│   │   └── sql-optimization-patterns.md  # SQL query optimization
│   └── opencode.json                     # Main opencode configuration
├── AGENTS.md                             # Agent configuration documentation
├── clippy.toml                           # Rust linter configuration
├── docs/                                 # Additional documentation
│   ├── AGENTS.md                         # Detailed agent documentation
│   └── information.md                    # Project information
├── LICENSE                               # Project license
├── README.md                             # This file
├── rustfmt.toml                          # Rust formatter configuration
└── start.sh                              # Setup script
```

## License

See the [LICENSE](LICENSE) file for details.
