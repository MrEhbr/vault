# Permanent Notes

Permanent notes are the core of the Zettelkasten method. These are atomic, evergreen notes that capture single ideas in your own words and connect to other notes, building your knowledge network over time.

## What Goes Here

- **Technical Concepts**: Individual programming and engineering concepts
- **Design Patterns**: Software patterns and architectural approaches
- **Mental Models**: Frameworks for understanding the world
- **Arguments**: Well-reasoned positions on technical and non-technical topics
- **Insights**: Personal realizations and discoveries from your experience
- **Definitions**: Clear explanations of important terms and concepts

## Software Engineering Notes to Start With

- **Programming Concepts**: Core concepts in languages you use
- **Architectural Patterns**: Approaches to system design
- **Technical Decision Records**: Reasoning behind important technical choices
- **Problem-Solution Pairs**: Recurring problems and their solutions
- **Code Insights**: Discoveries about coding approaches and techniques

## How to Create Permanent Notes

1. **Make atomic notes**: One idea per note
2. **Use a unique ID**: Use a timestamp (YYYYMMDD-HHMM) prefix
3. **Write in your own words**: Don't just copy/paste information
4. **Connect extensively**: Link to related notes
5. **Keep it evergreen**: These notes should remain relevant over time
6. **Start with technical concepts**: Begin with your area of expertise
7. **Expand beyond software**: Gradually add notes on other topics

## Permanent Note Structure Example

```markdown
# 20230515-1042 API Rate Limiting Strategies

Rate limiting is a technique to control the amount of requests a client can make to an API within a specified time window. Proper implementation prevents abuse and ensures fair resource allocation.

## Implementation Approaches
- **Token Bucket**: Clients consume tokens for each request, bucket refills at fixed rate
- **Leaky Bucket**: Requests processed at constant rate, excess requests queued or rejected
- **Fixed Window**: Count requests in fixed time intervals (e.g., 100 requests per minute)
- **Sliding Window**: More granular window that shifts with time
- **Distributed Rate Limiting**: Coordination across multiple API servers

## Considerations
- Rate limits should be per API key or user, not just by IP
- Different endpoints may need different limits based on resource intensity
- Clear documentation and response headers help API consumers understand limits
- 429 (Too Many Requests) status code with Retry-After header is the standard response

## Implementation Example (Go)
```go
// Simple token bucket example
func TokenBucket(requestCount, capacity, refillRate int) bool {
    // Implementation details
}
```

## Related Notes
- [[20230412-0930 API Design Principles]]
- [[20230501-1456 Service Resilience Patterns]]
- [[20230427-1145 HTTP Status Codes]]

## References
- [[Book: API Design Patterns]]
- [[Article: Scaling API Gateways]]
```

## Beyond Software Engineering

As your knowledge system grows, create permanent notes on:
- Personal productivity insights
- Learning and cognitive concepts
- Philosophical ideas
- Health and wellness discoveries
- Financial concepts
- Relationship insights
- Creative techniques

Permanent notes are the most valuable part of your knowledge system and become more useful as they connect to other notes across different domains of knowledge. 