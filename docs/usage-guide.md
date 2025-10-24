# Chatmode Files Usage Guide

This guide explains how to use and customize GitHub Copilot chatmode files from this repository.

## Table of Contents

- [What are Chatmode Files?](#what-are-chatmode-files)
- [How to Use Chatmode Files](#how-to-use-chatmode-files)
- [Customizing Chatmode Files](#customizing-chatmode-files)
- [Common Use Cases](#common-use-cases)
- [Troubleshooting](#troubleshooting)

## What are Chatmode Files?

Chatmode files (also known as custom instructions or agent files) are configuration files that customize GitHub Copilot's behavior for specific contexts. They allow you to:

- Define specialized knowledge domains
- Set coding standards and conventions
- Reference best practices and documentation
- Establish project-specific guidelines
- Configure code generation patterns

## How to Use Chatmode Files

### Method 1: GitHub Copilot Custom Instructions (Recommended)

GitHub Copilot supports custom instructions that can be defined at different scopes:

#### Project-Level Instructions

1. **Create a `.github` directory** in your project root (if it doesn't exist):
   ```bash
   mkdir -p .github
   ```

2. **Copy a chatmode file** from this repository to `.github/copilot-instructions.md`:
   ```bash
   # Example: Using the Python development chatmode
   cp chatmodes/examples/python-dev.md .github/copilot-instructions.md
   ```

3. **Customize the file** for your project needs (optional)

4. **Commit the file** to your repository:
   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add Copilot custom instructions"
   ```

GitHub Copilot will automatically detect and use these instructions when working in your project.

#### User-Level Instructions

For personal preferences across all projects:

1. Open GitHub Copilot settings in your IDE
2. Navigate to Custom Instructions
3. Paste the content from your chosen chatmode file
4. Save the settings

### Method 2: Direct Integration

For IDEs with advanced Copilot integration:

1. **Access Copilot Settings** in your IDE (VS Code, JetBrains, etc.)
2. **Find Custom Instructions or Chat Settings**
3. **Copy and paste** the chatmode file content
4. **Save and apply** the settings

### Method 3: Manual Reference

Use chatmode files as reference documentation:

1. Keep chatmode files open in a separate editor tab
2. Reference them when asking Copilot questions
3. Copy specific instructions as needed

## Customizing Chatmode Files

### Basic Customization

You can modify chatmode files to fit your specific needs:

#### Adding Project-Specific Rules

```markdown
# Original chatmode content here...

## Project-Specific Guidelines

- Use our internal logging library instead of console.log
- All API calls must use our custom fetch wrapper
- Follow our Git commit message convention: [TYPE] Message
```

#### Modifying Technology Stack

```markdown
## Technology Stack

This project uses:
- React 18 with TypeScript
- Tailwind CSS for styling
- React Query for data fetching
- Vitest for testing

Please follow patterns consistent with these technologies.
```

#### Adding Custom References

```markdown
## Internal Documentation

- [Team Coding Standards](https://internal-wiki.company.com/coding-standards)
- [Architecture Decisions](https://internal-wiki.company.com/adr)
- [API Documentation](https://internal-api-docs.company.com)
```

### Advanced Customization

#### Combining Multiple Chatmodes

You can combine instructions from multiple chatmode files:

```markdown
# Combined Development Assistant

<!-- Include Python best practices -->
[Content from python-dev.md]

<!-- Include Testing guidelines -->
[Content from testing-best-practices.md]

<!-- Include Security checks -->
[Content from security-focused.md]
```

#### Creating Domain-Specific Variations

Customize for your specific domain:

```markdown
# E-commerce Backend Developer

## Domain Context
This is an e-commerce application handling:
- Product catalog management
- Order processing
- Payment integration
- Inventory tracking

## Specific Requirements
- All monetary values use Decimal type, never float
- All database queries must be paginated
- PII data must be encrypted at rest
- Follow PCI DSS compliance for payment data
```

## Common Use Cases

### Use Case 1: New Project Setup

When starting a new project:

1. Choose a language/framework-specific chatmode
2. Copy it to your project's `.github` directory
3. Customize for your project's specific needs
4. Share with your team via version control

### Use Case 2: Code Reviews

Use specialized chatmodes during code reviews:

1. Load a code-review-focused chatmode
2. Ask Copilot to review code against best practices
3. Get suggestions for improvements

### Use Case 3: Learning New Technologies

When learning a new framework:

1. Use a framework-specific chatmode
2. Ask Copilot for explanations and examples
3. Get guidance following best practices

### Use Case 4: Security Audits

For security-focused development:

1. Load a security-focused chatmode
2. Ask Copilot to review code for vulnerabilities
3. Get recommendations for security improvements

### Use Case 5: Documentation Generation

For documentation tasks:

1. Use a documentation-focused chatmode
2. Ask Copilot to generate or improve documentation
3. Ensure consistency with documentation standards

## Best Practices for Using Chatmode Files

### 1. Start with Examples

- Begin with example chatmodes from this repository
- Understand how they work before customizing
- Build upon proven patterns

### 2. Keep Instructions Clear

- Use simple, direct language
- Break complex rules into bullet points
- Provide specific examples

### 3. Update Regularly

- Review and update chatmode files periodically
- Remove outdated references
- Add new best practices as they emerge

### 4. Version Control

- Commit chatmode files to your repository
- Track changes like any other code
- Document significant updates

### 5. Team Alignment

- Share chatmode files with your team
- Discuss and agree on customizations
- Use as part of onboarding documentation

## Troubleshooting

### Copilot Not Using Custom Instructions

**Problem**: Copilot doesn't seem to follow the chatmode file

**Solutions**:
1. Verify file is in correct location (`.github/copilot-instructions.md`)
2. Check file formatting is valid markdown
3. Restart your IDE
4. Ensure GitHub Copilot is up to date
5. Try being more explicit in your requests to Copilot

### Instructions Too Restrictive

**Problem**: Copilot is too constrained by the instructions

**Solutions**:
1. Review and simplify instructions
2. Use "when appropriate" or "prefer" instead of absolute requirements
3. Remove conflicting rules
4. Make instructions more context-specific

### Instructions Not Specific Enough

**Problem**: Copilot isn't following desired patterns

**Solutions**:
1. Add more specific examples
2. Be more explicit about requirements
3. Include code samples showing desired patterns
4. Break down complex requirements

### Conflicting Instructions

**Problem**: Different parts of the chatmode contradict each other

**Solutions**:
1. Review all instructions for conflicts
2. Prioritize and organize by importance
3. Remove or clarify conflicting rules
4. Test with specific scenarios

## Examples

### Example 1: Python Project

```markdown
# Python Development Assistant

## Project Context
Python 3.11+ web application using FastAPI

## Code Standards
- Follow PEP 8
- Use type hints for all functions
- Maximum line length: 88 characters (Black formatter)
- Use absolute imports

## Testing
- Use pytest for all tests
- Maintain >80% code coverage
- Write docstring examples that double as doctests

## Documentation
- Use Google-style docstrings
- Document all public APIs
- Include usage examples
```

### Example 2: React TypeScript Project

```markdown
# React TypeScript Development Assistant

## Project Context
React 18 + TypeScript + Tailwind CSS

## Component Guidelines
- Use functional components with hooks
- Props must have TypeScript interfaces
- Use named exports for components
- Co-locate styles with components

## State Management
- Use React Query for server state
- Use Context API for global UI state
- Avoid prop drilling with composition

## Testing
- Use React Testing Library
- Test user interactions, not implementation
- Mock API calls with MSW
```

## Getting More Help

- Check the [Best Practices Guide](best-practices.md)
- Review [Contributing Guide](contributing.md)
- Explore example chatmodes in `chatmodes/examples/`
- Open an issue for questions

## Additional Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Custom Instructions Guide](https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot)
- [Copilot Best Practices](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/)
