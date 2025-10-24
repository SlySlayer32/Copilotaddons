# Quick Reference Guide

A quick reference for using Copilot Addons chatmode files.

## 🚀 Quick Start (60 seconds)

1. **Browse chatmodes**: Check `chatmodes/examples/` for available files
2. **Copy to your project**: 
   ```bash
   mkdir -p .github
   cp chatmodes/examples/python-dev.md .github/copilot-instructions.md
   ```
3. **Start coding**: GitHub Copilot will automatically use these instructions

## 📁 Available Chatmode Files

### Examples (`chatmodes/examples/`)

| File | Purpose | Use When |
|------|---------|----------|
| `python-dev.md` | Python development with PEP 8 | Working on Python projects |
| `javascript-typescript-dev.md` | Modern JS/TS development | Working on JavaScript/TypeScript |
| `testing-best-practices.md` | Comprehensive testing | Writing or reviewing tests |
| `security-focused-dev.md` | Security-first development | Building secure applications |

### Templates (`chatmodes/templates/`)

- `chatmode-template.md` - Start here to create your own chatmode file

## 🎯 Common Use Cases

### For Python Development
```bash
cp chatmodes/examples/python-dev.md .github/copilot-instructions.md
```

### For React/TypeScript
```bash
cp chatmodes/examples/javascript-typescript-dev.md .github/copilot-instructions.md
# Then customize for React-specific patterns
```

### For Security Reviews
```bash
cp chatmodes/examples/security-focused-dev.md .github/copilot-instructions.md
```

### For Test-Driven Development
```bash
cp chatmodes/examples/testing-best-practices.md .github/copilot-instructions.md
```

## ✏️ Customizing Chatmodes

1. Copy a chatmode file to `.github/copilot-instructions.md`
2. Edit to add project-specific guidelines:
   ```markdown
   ## Project-Specific Rules
   
   - Use our custom logger: `import { logger } from './lib/logger'`
   - API calls must use our `apiClient` wrapper
   - All dates in UTC timezone
   ```
3. Commit to your repository

## 🤝 Contributing Your Own

1. Use the template: `chatmodes/templates/chatmode-template.md`
2. Fill in your domain-specific knowledge
3. Add examples and references
4. Place in `chatmodes/community/`
5. Submit a pull request

## 📚 Full Documentation

- [Complete Usage Guide](docs/usage-guide.md)
- [Best Practices Guide](docs/best-practices.md)
- [Contributing Guide](docs/contributing.md)

## 💡 Pro Tips

- **Combine chatmodes**: Merge multiple files for comprehensive coverage
- **Keep it focused**: Separate chatmodes for different concerns
- **Update regularly**: Keep references to docs and tools current
- **Test it**: Try your chatmode with real code before sharing
- **Share examples**: Include specific code examples for clarity

## 🔗 Useful Links

- [GitHub Copilot Docs](https://docs.github.com/en/copilot)
- [Custom Instructions](https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot)

---

Need more help? Open an issue or check the full documentation in the `docs/` directory.
