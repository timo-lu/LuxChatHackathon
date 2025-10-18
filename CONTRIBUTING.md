# Contributing to LuxChat Hackathon Documentation

Thank you for your interest in contributing! This document provides guidelines for adding and improving documentation in this repository.

## How to Contribute

### Adding New Documentation

1. **Choose the Right Location**
   - Main guides: `docs/` directory
   - External links: `docs/resources/external-links.md`
   - Diagrams: `docs/diagrams/`
   - Use the template: `docs/resources/TEMPLATE.md`

2. **Create Your Document**
   ```bash
   # Copy the template
   cp docs/resources/TEMPLATE.md docs/your-new-topic.md
   
   # Edit the file
   # Add your content following the template structure
   ```

3. **Update the Index**
   - Add a link to your new document in `docs/INDEX.md`
   - Place it in the appropriate section
   - Use a clear, descriptive title

4. **Follow Markdown Best Practices**
   - Use headers (#, ##, ###) for organization
   - Include code blocks with language specification
   - Add links to related documentation
   - Use lists for better readability

### Adding Diagrams

1. **Create the Diagram**
   - Use Mermaid for text-based diagrams (preferred)
   - Use Draw.io, Excalidraw, or similar tools for complex diagrams
   - Export as PNG or SVG

2. **Add to Repository**
   ```bash
   # Save diagram to docs/diagrams/
   # Use descriptive filename: system-architecture.png
   ```

3. **Reference in Documentation**
   ```markdown
   ![Diagram Description](./diagrams/your-diagram.png)
   ```

### Adding External Resources

1. Open `docs/resources/external-links.md`
2. Find the appropriate section
3. Add your link with format:
   ```markdown
   - [Resource Name](URL) - Brief description
   ```

### Improving Existing Documentation

1. **Fix Errors**
   - Typos, broken links, outdated information
   - Make the correction directly

2. **Enhance Content**
   - Add examples
   - Clarify confusing sections
   - Add diagrams or visuals
   - Include practical tips

3. **Keep It Current**
   - Update version numbers
   - Refresh deprecated information
   - Add new relevant resources

## Style Guidelines

### Markdown Formatting

- **Headers**: Use sentence case (capitalize first word only)
- **Code blocks**: Always specify the language
  ```javascript
  // Good
  ```
  
  ```
  // Avoid - no language specified
  ```

- **Links**: Use descriptive text, not "click here"
  ```markdown
  ✅ Check the [Matrix Protocol guide](./matrix-protocol.md)
  ❌ Click [here](./matrix-protocol.md) for Matrix Protocol
  ```

### Writing Style

- **Be Clear and Concise**: Get to the point quickly
- **Use Active Voice**: "The client sends a message" vs "A message is sent by the client"
- **Provide Context**: Explain why, not just what
- **Include Examples**: Show, don't just tell
- **Be Beginner-Friendly**: Don't assume too much knowledge

### Code Examples

- Include comments for clarity
- Show complete, working examples
- Indicate where placeholders should be replaced
- Test your code before adding it

```javascript
// Good example with context
// Replace 'YOUR_TOKEN' with your actual access token
const client = sdk.createClient({
  baseUrl: "https://matrix.org",
  accessToken: "YOUR_TOKEN",
  userId: "@user:matrix.org"
});
```

### Documentation Structure

Each document should have:

1. **Title**: Clear, descriptive
2. **Overview**: Brief introduction (1-2 paragraphs)
3. **Table of Contents**: For longer documents
4. **Main Content**: Organized with headers
5. **Resources**: Related links and documents
6. **Next Steps**: Guide readers to related content

## Commit Guidelines

### Commit Messages

Use clear, descriptive commit messages:

```
✅ Good:
- "Add WebSocket connection guide to development setup"
- "Fix broken link in Matrix protocol documentation"
- "Update API references with new endpoints"

❌ Avoid:
- "Update docs"
- "Fix stuff"
- "Changes"
```

### Commit Scope

- Keep commits focused on a single topic
- Group related changes together
- Separate different types of changes (fixes vs new content)

## Review Process

1. **Self-Review**
   - Read through your changes
   - Check all links work
   - Verify code examples
   - Test any commands or instructions

2. **Preview**
   - View your markdown in a renderer
   - Check formatting displays correctly
   - Ensure images load properly

3. **Cross-Reference**
   - Update related documents if needed
   - Check if INDEX.md needs updating
   - Verify internal links still work

## Tips for Quality Documentation

### Do's ✅

- ✅ Use real-world examples
- ✅ Link to official documentation
- ✅ Include diagrams and visuals
- ✅ Add troubleshooting sections
- ✅ Provide step-by-step instructions
- ✅ Keep it up to date

### Don'ts ❌

- ❌ Copy large sections from other sources without attribution
- ❌ Use absolute URLs for internal links (use relative paths)
- ❌ Add untested code examples
- ❌ Assume too much prior knowledge
- ❌ Leave TODO comments without following up
- ❌ Include sensitive information (tokens, passwords, etc.)

## Getting Help

If you're unsure about:

- Where to add something
- How to structure content
- Whether something is appropriate

Feel free to:
- Ask in the team chat
- Create an issue for discussion
- Start with a draft and ask for feedback

## Resources for Contributors

### Markdown
- [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/)
- [Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/)

### Mermaid Diagrams
- [Mermaid Documentation](https://mermaid.js.org/)
- [Mermaid Live Editor](https://mermaid.live/)

### Writing
- [Google Developer Documentation Style Guide](https://developers.google.com/style)
- [Microsoft Writing Style Guide](https://docs.microsoft.com/style-guide/)

## Recognition

All contributors are valued! Your contributions help make this resource better for everyone on the team.

## Questions?

If you have questions about contributing, please:
- Ask in the team communication channel
- Review existing documentation for examples
- Reach out to project maintainers

---

Thank you for contributing to the LuxChat Hackathon documentation! 🎉
