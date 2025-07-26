# Oqtane Module Context Engineering Template

Context engineering is the new way to build Oqtane modules - it's the way to actually make AI coding assistants work. Claude Code is the best for this so that's what this repo is centered around, but you can apply this strategy with any AI coding assistant!

A comprehensive template for getting started with Context Engineering for Oqtane CMS modules - the discipline of engineering context for AI coding assistants so they have the information necessary to build complete, production-ready modules end to end.

Context Engineering is 10x better than prompt engineering and 100x better than vibe coding for Oqtane development.

## Quick Start

```bash
# 1. Clone this template
git clone https://github.com/your-username/oqtane-module-context-template.git
cd oqtane-module-context-template

# 2. Set up your module requirements (optional - template provided)
# Edit CLAUDE.md to add your project-specific Oqtane guidelines

# 3. Add examples (highly recommended)
# Place relevant Oqtane module examples in the examples/ folder

# 4. Create your initial module request
# Edit INITIAL.md with your module requirements

# 5. Generate a comprehensive PRP (Product Requirements Prompt)
# In Claude Code, run:
/generate-prp INITIAL.md

# 6. Execute the PRP to implement your module
# In Claude Code, run:
/execute-prp PRPs/your-module-name.md
```

## Table of Contents

- [What is Context Engineering?](#what-is-context-engineering)
- [Template Structure](#template-structure)
- [Step-by-Step Guide](#step-by-step-guide)
- [Writing Effective INITIAL.md Files](#writing-effective-initialmd-files)
- [The PRP Workflow](#the-prp-workflow)
- [Using Examples Effectively](#using-examples-effectively)
- [Oqtane-Specific Best Practices](#oqtane-specific-best-practices)

## What is Context Engineering?

Context Engineering represents a paradigm shift from traditional Oqtane module development:

**Traditional Oqtane Development:**
- Copy existing module templates manually
- Replace tokens like `[Owner]`, `[Module]`, `[Description]`
- Requires deep knowledge of Oqtane architecture
- Prone to missing security, localization, or migration patterns
- Like giving someone a template and hoping they fill it out correctly

**Context Engineering:**
- A complete system for providing comprehensive Oqtane context
- Includes documentation, examples, patterns, security rules, and validation
- AI understands the full Oqtane ecosystem and best practices
- Like having an expert Oqtane developer with perfect memory

### Why Context Engineering for Oqtane?

- **Reduces Module Failures**: Most Oqtane module issues aren't code failures - they're missing context about security, migrations, or localization
- **Ensures Oqtane Compliance**: AI follows proper Oqtane patterns, inheritance hierarchies, and security models
- **Enables Complex Modules**: AI can handle multi-entity modules with relationships, advanced UI, and integrations
- **Self-Correcting**: Validation loops allow AI to fix Oqtane-specific issues automatically

## Template Structure

```
oqtane-module-context-template/
├── .claude/
│   ├── commands/
│   │   ├── generate-prp.md        # Generates Oqtane-specific PRPs
│   │   └── execute-prp.md         # Executes PRPs to build modules
│   └── settings.local.json        # Claude Code permissions
├── PRPs/
│   ├── templates/
│   │   └── oqtane_module_prp.md  # Base template for Oqtane PRPs
│   └── EXAMPLE_todo_module_prp.md # Example of a complete module PRP
├── examples/                      # Your Oqtane module examples (critical!)
│   ├── README.md                  # Explains each pattern
│   ├── basic-crud/               # Simple CRUD module
│   ├── advanced-features/        # Complex module with relationships
│   ├── security-patterns/        # Authorization examples
│   └── migration-examples/       # Database migration patterns
├── oqtane-docs/
│   ├── module-development.md     # Oqtane development guide
│   ├── security-guide.md         # Permission and authorization
│   ├── localization-guide.md     # Multi-language support
│   └── deployment-guide.md       # Module packaging and installation
├── CLAUDE.md                     # Global rules for Oqtane development
├── INITIAL.md                    # Template for module requests
├── INITIAL_EXAMPLE.md            # Example ToDo module request
└── README.md                     # This file
```

This template doesn't focus on RAG and tools with context engineering because there's a LOT more in store for that soon. ;)

## Step-by-Step Guide

### 1. Understanding CLAUDE.md

The `CLAUDE.md` file contains project-wide rules that the AI assistant will follow in every Oqtane development conversation. The template includes:

- **Oqtane Architecture**: 4-project structure, base classes, inheritance patterns
- **Security Requirements**: Authorization attributes, permission checks, ModuleId validation
- **Database Patterns**: Entity Framework contexts, migrations, IAuditable implementation
- **UI Standards**: Blazor component patterns, localization, responsive design
- **Code Quality**: File organization, naming conventions, error handling

You can use the provided template as-is or customize it for your specific Oqtane installation.

### 2. Creating Your Module Request

Edit `INITIAL.md` to describe your Oqtane module:

```markdown
## MODULE DETAILS:
**Name:** [Your module name]
**Owner/Namespace:** [Your company/namespace]
**Description:** [What this module does]

## FUNCTIONALITY:
[Describe specific features - be detailed about CRUD operations, UI components, business logic]

## DATABASE REQUIREMENTS:
[List entities, relationships, indexes needed]

## USER INTERFACE:
[Describe pages, forms, lists, settings - reference Oqtane UI patterns]

## EXAMPLES:
[List any example files in the examples/ folder and explain how they should be used]

## OQTANE SPECIFIC REQUIREMENTS:
[Security levels, localization, permissions, module settings]

## OTHER CONSIDERATIONS:
[Mention any gotchas, integrations, or things AI assistants commonly miss in Oqtane]
```

See `INITIAL_EXAMPLE.md` for a complete ToDo module example.

### 3. The PRP Workflow

PRPs (Product Requirements Prompts) are comprehensive Oqtane module blueprints that include:

- Complete Oqtane architecture context and patterns
- Step-by-step implementation with Oqtane validation
- Security and authorization requirements
- Database migration and entity patterns
- Localization and UI requirements
- Testing and deployment instructions

**Generate a PRP:**
```bash
# Run in Claude Code:
/generate-prp INITIAL.md
```

**Note:** The slash commands are custom commands defined in `.claude/commands/`. You can view their implementation:
- `.claude/commands/generate-prp.md` - See how it researches Oqtane patterns and creates PRPs
- `.claude/commands/execute-prp.md` - See how it builds complete modules from PRPs

The `$ARGUMENTS` variable in these commands receives whatever you pass after the command name (e.g., `INITIAL.md` or `PRPs/your-module.md`).

This command will:
- Read your module request
- Research the codebase for Oqtane patterns
- Search for relevant Oqtane documentation
- Create a comprehensive PRP in `PRPs/your-module-name.md`

**Execute the PRP:**
```bash
# Once generated, execute the PRP to build your module:
/execute-prp PRPs/your-module-name.md
```

The AI coding assistant will:
- Read all Oqtane context from the PRP
- Create a detailed implementation plan
- Build all 4 projects (Client, Server, Shared, Package)
- Implement database migrations with proper entity builders
- Add security, localization, and validation
- Run tests and fix any Oqtane-specific issues
- Create NuGet package ready for deployment

## Writing Effective INITIAL.md Files

### MODULE DETAILS: Be specific about Oqtane context
- ❌ "Build a blog module"
- ✅ "Build a multi-author blog module with categories, tags, SEO optimization, and RSS feeds that integrates with Oqtane's user management and supports multi-site installations"

### FUNCTIONALITY: Leverage specific Oqtane features
- Reference Oqtane components (Pager, ActionLink, AuditInfo)
- Specify security levels (View, Edit, Admin)
- Detail integration points (user management, file management, notifications)

### DATABASE REQUIREMENTS: Follow Oqtane patterns
- Always implement IAuditable on entities
- Include proper foreign keys to ModuleId
- Specify indexes for performance
- Plan for multi-tenant scenarios

### EXAMPLES: Reference the examples/ folder
- Place relevant Oqtane module patterns in `examples/`
- Reference specific files and patterns to follow
- Explain what aspects should be mimicked vs. customized

### OQTANE SPECIFIC REQUIREMENTS: Critical for success
- Security permissions and authorization levels
- Localization languages and resource keys
- Module settings and configuration options
- Integration with Oqtane's built-in features

## The PRP Generation Process

The `/generate-prp` command follows this process:

1. **Research Phase**
   - Analyzes your codebase for Oqtane patterns
   - Searches for similar module implementations
   - Identifies Oqtane conventions to follow

2. **Documentation Gathering**
   - Fetches relevant Oqtane API documentation
   - Includes security and localization guides
   - Adds common pitfalls and gotchas

3. **Blueprint Creation**
   - Creates step-by-step implementation plan
   - Includes Oqtane-specific validation gates
   - Adds migration, security, and test requirements

4. **Quality Check**
   - Scores confidence level (1-10)
   - Ensures all Oqtane context is included
   - Validates against known patterns

### PRP Execution Process

The `/execute-prp` command follows this workflow:

1. **Load Context**: Reads the entire PRP with all Oqtane patterns
2. **Plan**: Creates detailed task list for all 4 projects
3. **Execute**: Implements each component following Oqtane standards
4. **Validate**: Runs tests, checks migrations, validates security
5. **Iterate**: Fixes any Oqtane-specific issues found
6. **Package**: Creates NuGet package ready for deployment

See `PRPs/EXAMPLE_todo_module_prp.md` for a complete example of what gets generated.

## Using Examples Effectively

The `examples/` folder is critical for Oqtane success. AI coding assistants perform much better when they can see Oqtane patterns to follow.

### Essential Example Categories:

**Basic CRUD Patterns**
- Simple entity with standard operations
- Proper controller inheritance (ModuleControllerBase)
- Repository patterns with Entity Framework
- Basic Blazor components (Index, Edit, Settings)

**Advanced Module Features**
- Multi-entity relationships
- Complex business logic in managers
- Advanced UI components and interactions
- Integration with Oqtane services

**Security Patterns**
- Authorization attribute usage
- Permission checking in controllers
- ModuleId validation for security
- User context and claims handling

**Database Patterns**
- Migration entity builders
- Complex entity relationships
- Index creation and optimization
- Multi-tenant considerations

**Localization Examples**
- Resource file organization (.resx)
- Localized component examples
- Multi-language form validation
- Cultural formatting (dates, numbers)

```
examples/
├── README.md                     # Explains what each example demonstrates
├── basic-crud/                   # Simple CRUD module
│   ├── Client/                   # Blazor components and services
│   ├── Server/                   # Controllers, repositories, migrations
│   ├── Shared/                   # Models and interfaces
│   └── Package/                  # NuGet packaging
├── advanced-features/            # Complex module example
│   ├── multi-entity-relationships/
│   ├── advanced-ui-components/
│   └── business-logic-patterns/
├── security-patterns/            # Authorization examples
├── localization-examples/        # Multi-language support
└── migration-patterns/          # Database evolution examples
```

## Oqtane-Specific Best Practices

### Security First
- Always inherit from `ModuleControllerBase` in API controllers
- Use `[Authorize(Policy = PolicyNames.ViewModule)]` and `[Authorize(Policy = PolicyNames.EditModule)]`
- Validate `ModuleId` in all operations using `IsAuthorizedEntityId()`
- Never trust client-side data - validate on server

### Database Design
- All entities must implement `IAuditable` interface
- Include `ModuleId` foreign key for multi-tenant support
- Use Oqtane's migration system with proper entity builders
- Plan for database provider independence (SQL Server, MySQL, PostgreSQL, SQLite)

### UI/UX Standards
- Inherit Blazor components from `ModuleBase`
- Use Oqtane's built-in components (Pager, ActionLink, AuditInfo)
- Implement proper loading states and error handling
- Follow responsive design principles

### Localization Requirements
- Create `.resx` files for all user-facing text
- Support at minimum English (en) localization
- Use `IStringLocalizer<T>` in components
- Test with multiple cultures

### Performance Considerations
- Use async/await for all database operations
- Implement proper pagination with Oqtane's Pager component
- Add database indexes on frequently queried columns
- Dispose of resources properly

### Common AI Assistant Pitfalls to Avoid

**Don't assume the AI knows Oqtane specifics:**
- Include explicit Oqtane inheritance requirements
- Specify security attribute usage
- Detail migration entity builder patterns

**Include comprehensive examples:**
- More Oqtane examples = better implementations
- Show both what to do AND what not to do
- Include error handling and edge cases

**Validation is critical:**
- PRPs include test commands that must pass
- AI will iterate until all Oqtane validations succeed
- This ensures working modules on first deployment

**Documentation specificity:**
- Include official Oqtane documentation links
- Reference specific API methods and patterns
- Add version-specific considerations

### Module Quality Checklist

- [ ] All 4 projects build successfully
- [ ] Database migrations run up and down cleanly
- [ ] All controllers have proper authorization
- [ ] Entities implement IAuditable correctly
- [ ] Localization resources are complete
- [ ] Module installs and uninstalls properly
- [ ] NuGet package contains all required files
- [ ] Security permissions work as expected
- [ ] UI is responsive and accessible
- [ ] All CRUD operations function correctly

This Context Engineering approach ensures your Oqtane modules are production-ready, secure, and follow all best practices from day one!