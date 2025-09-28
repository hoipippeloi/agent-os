# Agent OS

**Stop prompting AI coding agents like it's 2024**

Your coding agents are capable of so much more—they just need an operating system. Agent OS transforms AI coding agents from confused interns into productive developers with structured workflows that capture your standards, your stack, and the unique details of your codebase.

## What is Agent OS?

Agent OS is a system for better planning and executing software development tasks with AI agents. It provides three layers of context that work together to ensure agents write code that looks like you wrote it—first time, every time.

### Compatible with:
- ✅ Claude Code, Cursor, or any other AI coding tool
- ✅ New products or established codebases  
- ✅ Big features, small fixes, or anything in between
- ✅ Any language or framework

## Why Use Agent OS?

### 1. Complete Context, Not Just Prompts
Unlike basic AI setups, Agent OS provides three layers of context:
- **Standards** - Your coding style, tech stack, and best practices
- **Product** - Your mission, architecture, roadmap, and decisions  
- **Specs** - Detailed plans & tasks for each feature implementation

### 2. Structured Development, Not Chaos
Agent OS replaces random prompting with a proven workflow that automatically:
- Writes comprehensive specs before coding begins
- Breaks features into trackable, TDD-focused tasks
- Documents key decisions as they happen
- Updates your roadmap as features ship

### 3. Your Standards, Your Way
Completely customizable through markdown files you control. Define your own coding standards, write custom instructions, and adapt every workflow to match how your team operates.

## The Three Layers of Context

### Layer 1: Your Standards
Global standards that define how you build software across all projects:
- **Tech Stack** — Your default frameworks, libraries, and tools
- **Code Style** — Your formatting rules, naming conventions, and preferences  
- **Best Practices** — Your development philosophy (e.g., TDD, commit patterns, etc.)

*Location: `~/.agent-os/standards/` (global) and `.agent-os/standards/` (project-specific)*

### Layer 2: Your Product
Product-specific context about what you're building:
- **Mission** — What you're building, for whom, and why it matters
- **Roadmap** — Features shipped, in progress, and planned
- **Decisions** — Key architectural and technical choices (with rationale)
- **Product-specific stack** — The exact versions and configurations for this codebase

*Location: `.agent-os/product/` in your project*

### Layer 3: Your Specs
Individual feature specifications for each development task:
- **SRD (Spec Requirements Document)** — Goals, user stories, success criteria
- **Technical Specs** — API design, database changes, UI requirements
- **Tasks Breakdown** — Step-by-step implementation plan with dependencies

*Location: `.agent-os/specs/YYYY-MM-DD-feature-name/` in your project*

## Installation

Agent OS has a flexible two-part installation system:

### 1. Base Installation (Recommended)
Install Agent OS centrally on your system to maintain default standards and instructions.

**Navigate to your home directory:**
```bash
cd ~
```

**Choose your installation based on tools you use:**

For Claude Code:
```bash
curl -sSL https://raw.githubusercontent.com/buildermethods/agent-os/main/setup/base.sh | bash -s -- --claude-code
```

For Cursor:
```bash
curl -sSL https://raw.githubusercontent.com/buildermethods/agent-os/main/setup/base.sh | bash -s -- --cursor
```

For both Claude Code & Cursor:
```bash
curl -sSL https://raw.githubusercontent.com/buildermethods/agent-os/main/setup/base.sh | bash -s -- --claude-code --cursor
```

**What this installs:**
- Creates `.agent-os/` folder in your home directory
- Downloads instruction files (plan-product, create-spec, execute-tasks, etc.)
- Downloads standards templates (tech-stack, code-style, best-practices)
- Downloads language-specific code style guides
- Creates `config.yml` for version tracking
- Sets up project installation script
- Installs Claude Code agents (if selected)

### 2. Project Installation
Install Agent OS into each project you work on:

```bash
# Navigate to your project root
cd /path/to/your/project

# Run the project installation
~/.agent-os/setup/project.sh
```

**What this installs:**
- Creates `.agent-os/` folder in your project
- Copies standards from your base installation
- Creates product documentation templates
- Sets up spec workflow structure
- Configures project-specific settings

## Manual Installation

If you prefer manual setup:

### Base Installation
```bash
# Create directories
mkdir -p ~/.agent-os/standards/code-style
mkdir -p ~/.agent-os/instructions/core
mkdir -p ~/.agent-os/instructions/meta
mkdir -p ~/.agent-os/commands
mkdir -p ~/.agent-os/setup

# Copy files from this repository to appropriate locations
# See repository structure for file locations
```

### Project Installation
```bash
# In your project root
mkdir -p .agent-os/product
mkdir -p .agent-os/specs
mkdir -p .agent-os/standards

# Copy standards from base installation
cp -r ~/.agent-os/standards/* .agent-os/standards/

# Create product documentation files
touch .agent-os/product/mission.md
touch .agent-os/product/roadmap.md
touch .agent-os/product/decisions.md
touch .agent-os/product/tech-stack.md
```

## Core Workflow Commands

Agent OS provides structured commands for development workflow:

### 1. Plan Product (`plan-product`)
- Analyze your product vision and goals
- Create or update mission.md and roadmap.md
- Establish product-level context

### 2. Create Spec (`create-spec`)
- Generate comprehensive feature specifications
- Create SRD (Spec Requirements Document)
- Break down into actionable tasks
- Plan technical implementation

### 3. Execute Tasks (`execute-tasks`)
- Implement features following the spec
- Update roadmap as tasks complete
- Document decisions made during development
- Maintain code quality standards

### 4. Analyze Product (`analyze-product`)
- Review current state of your product
- Identify gaps and opportunities
- Update roadmap and priorities

## File Structure

After installation, your project will have this structure:

```
your-project/
├── .agent-os/
│   ├── product/
│   │   ├── mission.md          # What you're building and why
│   │   ├── roadmap.md          # Features and development phases
│   │   ├── decisions.md        # Key architectural decisions
│   │   └── tech-stack.md       # Project-specific technologies
│   ├── specs/
│   │   └── YYYY-MM-DD-feature-name/
│   │       ├── srd.md          # Spec Requirements Document
│   │       ├── technical-spec.md # Technical implementation details
│   │       └── tasks.md        # Task breakdown
│   └── standards/
│       ├── tech-stack.md       # Your technology preferences
│       ├── code-style.md       # Coding conventions
│       ├── best-practices.md   # Development philosophy
│       └── code-style/
│           ├── javascript-style.md
│           ├── css-style.md
│           └── html-style.md
├── llms.txt                    # LLM documentation (required)
├── docs/                       # User documentation
├── tests/                      # Test scripts
└── tasks.md                    # Current project tasks
```

## Using Agent OS

### Starting a New Feature

1. **Create Spec**: Use `create-spec` command to plan your feature
2. **Review Plan**: Examine the generated SRD and technical specs
3. **Execute Tasks**: Use `execute-tasks` to implement the feature
4. **Update Documentation**: Roadmap and decisions are updated automatically

### Best Practices

#### Review Plans Carefully
- The planning phase is crucial—invest time here to save time later
- Review the SRD and task breakdown before execution
- Ensure alignment on approach before coding begins

#### Start Small
- Don't try to document everything at once
- Begin with basic standards, refine as you go

#### Be Specific in Standards
- ❌ "Use PostgreSQL" 
- ✅ "Use PostgreSQL 15+ with schemas for multi-tenancy"
- ❌ "Write tests"
- ✅ "Write unit tests first, aim for 80% coverage"

#### Trust the Process
- Let your agent own entire features, not just snippets
- Review and refine rather than micromanage

#### Know When to Start Fresh
- Not happy with implementation? Revert and redo with better planning
- Clear redo usually beats incremental fixes

## Customization and Refinement

### Standards Files
Regularly update your standards based on:
- Patterns you see in code reviews
- New best practices your team adopts
- Technology updates and preferences

### Product Files
Keep product documentation current:
- Update `roadmap.md` as features ship
- Document important decisions in `decisions.md`
- Adjust `mission.md` as product evolves

### Making Refinements Stick
- Be specific in your documentation
- Include code examples showing good/bad patterns
- Explain why one approach is preferred
- Version your changes with brief changelogs

## Context Management

Agent OS uses smart context management for optimal performance:

- **Conditional Loading**: Files only load when needed for current task
- **Lite Files**: Condensed versions for efficient context usage
- **Context-Aware Instructions**: Standards load relevant sections only
- **60-80% Context Reduction**: Compared to loading everything upfront

## Claude Code Integration

If using Claude Code, Agent OS automatically uses specialized subagents:

- **test-runner**: Runs and analyzes test failures
- **context-fetcher**: Efficiently retrieves relevant documentation  
- **git-workflow**: Handles branches, commits, and pull requests
- **file-creator**: Creates multiple files and directories in batch

## Troubleshooting

### Agent Not Following Your Style?
- Check that standards files are specific enough
- Add examples to `code-style.md`
- Update `best-practices.md` with clear dos and don'ts

### Tasks Too Big or Too Small?
- Review task breakdown during `create-spec` phase
- Ask agent to adjust: "Break task 3 into smaller sub-tasks"
- Or: "Tasks 2 and 3 should be combined"

### Wrong Technical Approach?
- Review technical specs during planning phase
- Don't wait until code is written to course-correct
- Update `tech-stack.md`, `decisions.md`, or `best-practices.md`

## Requirements

### Project Requirements
- `llms.txt` file in project root (for LLM documentation)
- `docs/` folder for user documentation
- `tests/` folder for test scripts  
- `tasks.md` file for current project tasks

### Environment Files
- Always read environment files with CLI tools
- Never include keys/passwords in LLM documentation

## License

Agent OS is free and open source, released under the MIT license.

## Created By

Agent OS is created by [Brian Casel](https://buildermethods.com), creator of Builder Methods.

**Free Resources:**
- [Builder Briefing Newsletter](https://buildermethods.com)
- [YouTube Channel](https://youtube.com/@briancasel)
- [Agent OS Documentation](https://buildermethods.com/agent-os)

---

*For the most up-to-date documentation and installation instructions, visit [buildermethods.com/agent-os](https://buildermethods.com/agent-os)*
