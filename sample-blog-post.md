---
title: "Sample Blog Post Title"
date: 2026-01-05T10:00:00-05:00
excerpt: "This is a sample blog post demonstrating the structure and markdown features available for your Hugo blog. Use this as a template for creating your own posts."
tags: ["tutorial", "getting-started", "sample"]
draft: false
---

## Introduction

This is a sample blog post that demonstrates the structure and various markdown features you can use when writing blog posts for your Hugo site. Feel free to use this as a template or reference when creating your own content.

## Text Formatting

You can use **bold text** for emphasis, *italic text* for subtle emphasis, and ***bold italic*** for strong emphasis. You can also use `inline code` for technical terms or code snippets.

## Headings Structure

### This is a Level 3 Heading

Your content can be organized using different heading levels. The post title is H1, so start your content sections with H2 (##) and use H3 (###) and beyond for subsections.

#### This is a Level 4 Heading

Even more specific subsections can use H4 headings.

## Lists

### Unordered Lists

Here's an example of a bulleted list:

- First item
- Second item with more detail
- Third item
  - Nested item 1
  - Nested item 2
- Fourth item

### Ordered Lists

And here's a numbered list:

1. First step
2. Second step
3. Third step
   1. Sub-step A
   2. Sub-step B
4. Fourth step

## Code Examples

### Inline Code

When referencing commands or code inline, use backticks: `npm install`, `docker build`, `kubectl get pods`.

### Code Blocks

For larger code snippets, use fenced code blocks with syntax highlighting:

```bash
# Example bash commands
cd /path/to/project
npm install
npm run build
```

```yaml
# Example YAML configuration
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376
```

```javascript
// Example JavaScript code
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("World"));
```

## Links and References

You can add links to external resources: [Hugo Documentation](https://gohugo.io/documentation/)

Or create reference-style links for cleaner markdown:

Check out the [Kubernetes docs][k8s] and [Docker documentation][docker] for more information.

[k8s]: https://kubernetes.io/docs/
[docker]: https://docs.docker.com/

## Blockquotes

Use blockquotes for highlighting important information or quotes:

> This is a blockquote. It's useful for highlighting important points, quotes from other sources, or key takeaways from your content.

## Images

To add images, place them in the `static/images/` directory and reference them like this:

```markdown
![Alt text description](/images/your-image.png)
```

## Tables

You can also create tables (though they're best used sparingly):

| Feature | Description | Status |
|---------|-------------|--------|
| Markdown | Full markdown support | ✓ |
| Code Blocks | Syntax highlighting | ✓ |
| Tags | Categorization | ✓ |
| Draft Mode | Hide unpublished posts | ✓ |

## Horizontal Rules

Use three or more hyphens, asterisks, or underscores for horizontal rules:

---

## Conclusion

This sample post demonstrates the key markdown features available for your blog posts. When creating your own posts:

1. Create a new `.md` file in `content/blog/`
2. Add frontmatter with title, date, excerpt, and tags
3. Write your content using markdown
4. Set `draft: false` when ready to publish
5. The Hugo server will automatically rebuild and show your new post

Feel free to modify or delete this sample post once you're comfortable with the blog post structure!
