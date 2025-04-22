# Resources

Resources are collections of reference materials and information on topics of interest. This is where you store knowledge that isn't project-specific or fleeting, creating a personal reference library.

## What Goes Here

- **Technical Documentation**: Language references, framework guides, API documentation
- **Topic Collections**: Information about technical and non-technical subjects
- **Book Notes**: Summaries and notes from books you've read
- **Article Collections**: Summaries and excerpts from articles
- **Course Notes**: Notes from courses, workshops, or seminars
- **How-to Guides**: Instructions and processes for future reference
- **Code Snippets**: Reusable code patterns and solutions
- **Cheatsheets**: Quick reference materials for languages, tools, and concepts

## Software Engineering Resources to Start With

- **Language Documentation**: References for programming languages you use
- **Design Patterns**: Common patterns and their implementations
- **Algorithms**: Explanations and implementations of algorithms
- **System Architecture**: References on architecture patterns and principles
- **Development Tools**: Notes on tools, IDEs, and environments
- **Code Standards**: Formatting, testing, and documentation standards
- **Solution Patterns**: Common approaches to recurring technical problems

## How to Organize Resources

1. Create top-level folders by general topic (e.g., Programming, Books, Travel)
2. Create subfolders for specific domains (e.g., Golang, Frontend, DevOps)
3. Use prefixes to indicate the type of resource (e.g., "Book:", "Article:")
4. Link resource notes to relevant permanent notes and MOCs
5. Tag resources for cross-cutting categorization

## Resource Note Structure Example

```markdown
# Effective Go

## Overview
Official documentation for writing clear, idiomatic Go code. This resource covers the essential patterns and practices for effective Go programming.

## Key Points
- Formatting and naming conventions
- Control structures and error handling patterns
- Concurrency patterns with goroutines and channels
- Interface design and implementation
- Memory management and optimization

## Important Sections
- Concurrency section explains Go's approach to handling concurrent operations
- Error handling section demonstrates idiomatic error handling
- Interface section shows how to use interfaces effectively

## Code Examples
```go
// Example of effective error handling in Go
if err := doSomething(); err != nil {
    return fmt.Errorf("failed to do something: %w", err)
}
```

## Related Notes
- [[20230412-1534 Go Concurrency Patterns]]
- [[20230501-0945 Error Handling Best Practices]]
- [[Go Project Structure]]

## References
- [Effective Go - golang.org](https://golang.org/doc/effective_go)
```

## Expanding Beyond Software Resources

As your knowledge system grows, add resources in other areas:
- **Books and Articles**: Notes on non-technical reading
- **Travel**: Guides, recommendations, and travel notes
- **Cooking**: Recipes, techniques, and meal planning
- **Health**: Medical information, fitness resources, nutrition guides
- **Finance**: Investment information, tax guides, financial planning
- **Hobbies**: Reference materials for personal interests

Resources provide the foundation of your knowledge repository and become more valuable as you connect them to your own insights and experiences. 