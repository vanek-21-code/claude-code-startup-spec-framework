# Contributing to Universal Startup Specification Framework

Thank you for your interest in contributing to this framework! This document provides guidelines for contributing.

## How to Contribute

### Reporting Issues
- Use the GitHub issue tracker to report bugs
- Include detailed steps to reproduce the issue
- Provide example inputs and expected vs actual outputs

### Suggesting Enhancements
- Use GitHub issues to suggest new features
- Clearly describe the enhancement and its benefits
- Include examples of how it would be used

### Code Contributions

#### Adding New Business Models
1. Update `business-model-generator.md` with new model patterns
2. Add corresponding feature patterns to `feature-generator.md`
3. Update `repository-structure-template.md` if needed
4. Add new schemas if required
5. Test with sample startups

#### Adding New Tech Stacks
1. Update `tech-architecture-generator.md` with new stack options
2. Add corresponding templates to `repository-structure-template.md`
3. Update `claude-instructions-generator.md` for new deployment patterns
4. Add tech-specific schemas if needed
5. Validate with test implementations

#### Improving Existing Modules
1. Review the module documentation
2. Ensure backward compatibility
3. Add tests for new functionality
4. Update documentation

## Development Process

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test your changes with the example
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

## Code Style

- Follow the existing documentation format
- Use clear, descriptive names for files and variables
- Include inline comments for complex logic
- Follow YAML formatting standards for schema files

## Testing

- Test all changes with the provided example
- Ensure generated repositories validate against schemas
- Verify Claude Code compatibility
- Test cross-module integration

## Pull Request Process

1. Update the README.md with details of changes if applicable
2. Update the CHANGELOG.md with your changes
3. Ensure all tests pass
4. Get approval from at least one maintainer
5. The PR will be merged once approved

## Community Guidelines

- Be respectful and constructive
- Focus on the technical merits of contributions
- Help others learn and improve
- Follow the code of conduct

## Questions?

Feel free to open an issue for any questions about contributing!