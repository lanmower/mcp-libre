# 📂 Repository Structure

This document explains the organization of the LibreOffice MCP Server repository.

## 🗂️ Directory Structure

```
mcp-libre/
├── 📁 src/                         # Source code
│   ├── __init__.py                 # Package initialization
│   ├── libremcp.py                 # Main MCP server implementation
│   └── main.py                     # Entry point script
├── 📁 tests/                       # Test files
│   ├── __init__.py                 # Test package initialization
│   ├── test_client.py              # Interactive MCP client test
│   └── test_insert_fix.py          # Specific function tests
├── 📁 examples/                    # Demo and example scripts
│   ├── __init__.py                 # Examples package initialization
│   ├── demo_editing.py             # Document editing demonstrations
│   └── demo_live_viewing.py        # Live viewing and editing demo
├── 📁 config/                      # Configuration templates
│   ├── claude_config.json.template # Claude Desktop configuration template
│   └── mcp.config.json.template    # Super Assistant configuration template
├── 📁 scripts/                     # Utility scripts
│   ├── generate-config.sh          # Configuration generator script
│   └── mcp-helper.sh               # Helper script for testing and setup
├── 📁 docs/                        # Documentation
│   ├── CHATGPT_BROWSER_GUIDE.md    # ChatGPT browser integration guide
│   ├── COMPLETE_SOLUTION.md        # Comprehensive overview
│   ├── EXAMPLES.md                 # Usage examples
│   ├── LICENSE_OPTIONS.md          # License information
│   ├── LIVE_VIEWING_GUIDE.md       # Live viewing setup guide
│   ├── PREREQUISITES.md            # System requirements
│   ├── QUICK_START.md              # Quick start guide
│   ├── REPOSITORY_STRUCTURE.md     # This file
│   ├── SUPER_ASSISTANT_SETUP.md    # Super Assistant setup guide
│   └── TROUBLESHOOTING.md          # Troubleshooting guide
├── 📄 README.md                    # Main project documentation
├── 📄 LICENSE                      # MIT License
├── 📄 pyproject.toml               # Python project configuration
├── 📄 uv.lock                      # UV dependency lock file
├── 📄 .gitignore                   # Git ignore rules
├── 📄 .python-version              # Python version specification
├── 🔧 mcp-helper.sh               # Wrapper for scripts/mcp-helper.sh
└── 🔧 generate-config.sh          # Wrapper for scripts/generate-config.sh
```

## 📋 File Descriptions

### Source Code (`src/`)
- **`libremcp.py`**: Core MCP server implementation with all tools and resources
- **`main.py`**: Entry point that imports and runs the MCP server
- **`__init__.py`**: Makes src a Python package and exposes the main function

### Tests (`tests/`)
- **`test_client.py`**: Interactive test client that demonstrates all MCP tools
- **`test_insert_fix.py`**: Specific tests for document text insertion functionality
- **`__init__.py`**: Test package initialization

### Examples (`examples/`)
- **`demo_editing.py`**: Comprehensive demo showing document editing capabilities
- **`demo_live_viewing.py`**: Demo of live document viewing and real-time editing
- **`__init__.py`**: Examples package initialization

### Configuration (`config/`)
- **`claude_config.json.template`**: Template for Claude Desktop MCP configuration
- **`mcp.config.json.template`**: Template for Super Assistant proxy configuration

### Scripts (`scripts/`)
- **`generate-config.sh`**: Generates personalized configuration files from templates
- **`mcp-helper.sh`**: Comprehensive helper script for testing, setup, and management

### Documentation (`docs/`)
- **Setup Guides**: Step-by-step instructions for different integration scenarios
- **Usage Examples**: Practical examples and use cases
- **Troubleshooting**: Common issues and solutions
- **Prerequisites**: System requirements and installation instructions

## 🚀 Quick Access

### Root Level Wrappers
For convenience, wrapper scripts are provided in the root directory:

```bash
# These are equivalent:
./mcp-helper.sh check          # Wrapper script
./scripts/mcp-helper.sh check  # Direct access

./generate-config.sh both      # Wrapper script  
./scripts/generate-config.sh both  # Direct access
```

### Running Components

```bash
# Run the MCP server directly
uv run python src/main.py

# Run tests
uv run python tests/test_client.py

# Run examples
uv run python examples/demo_editing.py

# Use helper scripts
./mcp-helper.sh test
./generate-config.sh claude
```

## 📦 Package Structure

The project follows Python packaging best practices:

- **Source code** is in `src/` (src layout)
- **Tests** are separate from source code
- **Examples** are clearly separated from core functionality
- **Configuration** templates are centralized
- **Scripts** are organized in their own directory
- **Documentation** is comprehensive and well-organized

## 🔧 Build and Installation

The `pyproject.toml` file is configured for the new structure:

```toml
[project.scripts]
mcp-libre = "src.libremcp:main"
```

This allows the package to be installed and run as:
```bash
uv pip install -e .  # Install in development mode
mcp-libre             # Run the installed script
```

## 🔍 Path Management

All scripts automatically handle the new directory structure:

- **generate-config.sh**: Uses `PROJECT_ROOT` to find templates and generate correct paths
- **mcp-helper.sh**: Uses `PROJECT_ROOT` to run tests and examples from correct locations
- **Test files**: Add `src/` to Python path automatically
- **Example files**: Add `src/` to Python path automatically

This ensures everything works regardless of where the repository is installed or how scripts are executed.
