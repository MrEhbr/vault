# Common Second Brain Workflows

This guide provides practical, concrete examples of how to use your second brain system in daily life, starting with software engineering but applicable to any domain.

## File Locations Quick Reference

| Type of Note | Where to Store It |
|--------------|-------------------|
| Daily notes | `07 - Daily/YYYY-MM-DD.md` |
| Inbox captures | `01 - Inbox/` (any filename) |
| Fleeting thoughts | `06 - Fleeting/` (any descriptive name) |
| Permanent notes | `05 - Permanent/YYYYMMDD-HHMM Title.md` |
| Project notes | `02 - Projects/Project Name/` |
| Resource notes | `04 - Resources/Category/Resource.md` |
| Maps of Content | `00 - Maps of Content/Topic MOC.md` |
| Assets/Attachments | `98 - Assets/` |
| Archives | `08 - Archives/` (completed projects) |

## 1. Daily Development Workflow

### Morning Capture (Technical Focus)

1. Open Obsidian
2. Create today's daily note (in 07 - Daily folder)
   • Use Daily Notes plugin or manually create YYYY-MM-DD.md
3. Review yesterday's open tasks and carry them forward
4. List today's priorities (meetings, coding tasks, reviews)
5. Open relevant project notes for context

**Example Daily Note Location:**
`07 - Daily/2023-06-15.md`

**Example Daily Note Start:**
```markdown
# Daily Note - 2023-06-15 (Thursday)

## Carry-over Tasks
- [ ] Finish API authentication implementation
- [ ] Review PR from Sarah on database indexing

## Today's Priorities
- [ ] Sprint planning meeting (10:00)
- [ ] Complete user authorization module
- [ ] Debug performance issue in search function
- [ ] Set up monitoring for new service

## Notes & Thoughts
...
```

### During the Day (Capture Mode)

1. When you solve a technical problem:
   - Quickly capture the solution in your daily note (07 - Daily)
   - Include error messages and code snippets
   - Tag with #solution #code

2. During/after meetings:
   - Take notes directly in your daily note (07 - Daily)
   - Mark action items with checkboxes [ ]
   - Tag with #meeting

3. When you encounter a useful concept:
   - Capture in Inbox (01 - Inbox) or Fleeting Notes (06 - Fleeting)
   - Include enough context to process later
   - Add #toprocess tag

**Example In-Day Capture in Daily Note:**
`07 - Daily/2023-06-15.md`

```markdown
## Notes & Thoughts

### JWT Implementation Issue (10:30am)
Error: `Token signature verification failed`
Solution: Had to synchronize server time with NTP
#solution #authentication

### Sprint Planning Notes (11:15am)
- New feature prioritized: Advanced search
- Database migration scheduled for next Tuesday
- My tasks: Finish auth system, help with search performance
- Team concerned about test coverage
- Action Items:
  - [ ] Complete auth system by Friday
  - [ ] Schedule pair programming with Alex on test improvement
#meeting #sprint
```

**Alternative: Quick Capture in Inbox:**
`01 - Inbox/JWT Authentication Issue.md`

### End of Day Processing (15 minutes)

1. Review the day's notes (in 07 - Daily)
2. Complete daily reflection
3. Format and organize any messy notes
4. Create permanent notes for important concepts (in 05 - Permanent)
5. Move project-specific notes to project files (in 02 - Projects)
6. Set tomorrow's preliminary tasks

**Example End-of-Day (in same Daily Note):**
`07 - Daily/2023-06-15.md`

```markdown
## Daily Reflection
- Good progress on auth system
- Learned about JWT token security best practices
- Need to improve meeting focus
- Tomorrow: Focus on completing auth system tests

## For Tomorrow
- [ ] Implement auth system unit tests
- [ ] Pair programming with Alex (2pm)
- [ ] Research monitoring solutions
```

## 2. Extracting Permanent Notes (Weekly Process)

### From Code Solutions to Permanent Notes

1. During weekly review, identify valuable solutions from daily notes (07 - Daily)
2. Create new note in Permanent Notes folder (05 - Permanent) with timestamp ID
3. Extract the core concept (not just the specific solution)
4. Add context and explanation in your own words
5. Link to related concepts
6. Tag appropriately

**Example Source (Daily Note):**
`07 - Daily/2023-06-15.md`

**Example Transformation to Permanent Note:**
`05 - Permanent/20230615-1435 JWT Token Time Sensitivity.md`

```markdown
# 20230615-1435 JWT Token Time Sensitivity

JWT tokens can fail validation when server times are not synchronized, as the token's `iat` (issued at) and `exp` (expiration) fields are time-dependent.

## Problem Signs
- "Token signature verification failed" errors
- Intermittent authentication issues
- Problems across multiple servers but not locally

## Solutions
- Implement NTP time synchronization across all servers
- Add clock skew tolerance in token validation
- Consider using longer token validity periods for non-critical applications

## Code Example

// Add tolerance for clock skew
tokenValidationParams := jwt.ValidationParameters{
    ClockSkew: time.Minute * 5,
    // other parameters
}

## Related Notes
- [[20230412-0930 Authentication Best Practices]]
- [[20230501-1456 Microservice Time Synchronization]]
- [[JWT Structure and Security]]

## References
- [[Article: JWT Common Pitfalls]]
```

## 3. Project Knowledge Management Flow

### Setting Up a New Coding Project

1. Create project folder in Projects directory (02 - Projects/Project Name)
2. Create project index note with metadata
3. Set up standard sections (overview, architecture, decisions)
4. Link to relevant resources and references
5. Create initial task list

**Example Project Setup:**
`02 - Projects/E-commerce API Modernization/E-commerce API Modernization.md`

```markdown
# Project: E-commerce API Modernization

## Overview
- Start date: 2023-06-15
- Target completion: 2023-09-30
- Goal: Replace monolithic API with microservices architecture
- Team: @Alex (Frontend), @Sarah (DB), @Me (Backend)

## Architecture
- Microservices with API gateway
- Event-driven communication
- PostgreSQL for persistence
- Redis for caching
![[ecommerce-architecture-diagram.png]]

## Technical Decisions
- [[Decision Record: Service Boundaries]]
- [[Decision Record: Authentication Approach]]
- [[Decision Record: Database Schema]]

## Development Tasks
- [ ] Define service boundaries
- [ ] Create API gateway
- [ ] Implement auth service
- [ ] Migrate product catalog
- [ ] Implement order processing

## Resources
- [[Book: Building Microservices]]
- [[Internal: Legacy System Documentation]]
- [[Article: API Gateway Patterns]]
```

**Associated Architecture Diagram:**
`98 - Assets/ecommerce-architecture-diagram.png`

### Documenting Technical Decisions

1. When making significant decisions:
   - Create note in project folder (02 - Projects/Project Name/)
   - Document context, options, decision, and rationale
   - Link to relevant permanent notes
   - Link from project index

**Example Decision Record:**
`02 - Projects/E-commerce API Modernization/Decision Record - Authentication Approach.md`

```markdown
# Decision Record: Authentication Approach

## Context
The new microservices architecture requires a centralized authentication system.

## Options Considered
1. **Session-based auth with Redis**
   - Pros: Familiar, easy revocation
   - Cons: State management across services, scaling issues

2. **JWT-based auth**
   - Pros: Stateless, good for microservices
   - Cons: Token size, revocation challenges

3. **OAuth 2.0 with external provider**
   - Pros: Standardized, delegation support
   - Cons: Complexity, external dependency

## Decision
Implement **JWT-based authentication** with a dedicated Auth Service

## Rationale
- Fits well with stateless microservices architecture
- Reduces cross-service communication for auth checks
- Simpler to implement than OAuth initially
- Can migrate to OAuth provider later if needed

## Implementation Notes
- Auth service will issue and validate tokens
- Short expiry with refresh tokens for security
- Use Redis for refresh token storage and revocation
- See [[20230615-1435 JWT Token Time Sensitivity]] for implementation concerns

## Status
Approved - 2023-06-17
```

## 4. Learning Flow - From Resources to Knowledge

### Technical Book Processing

1. Create note in Resources/Books folder (04 - Resources/Books/)
2. Take progressive notes while reading
3. Highlight key concepts, code examples, insights
4. During weekly review:
   - Extract concepts to permanent notes (05 - Permanent)
   - Connect to existing knowledge
   - Update relevant MOCs (00 - Maps of Content)

**Example Book Resource:**
`04 - Resources/Books/Designing Data-Intensive Applications.md`

```markdown
# Book: Designing Data-Intensive Applications

## Chapter 1: Reliable, Scalable, and Maintainable Applications
- Reliability: System works correctly even with faults
- Scalability: Ability to handle growth (load)
- Maintainability: Different people can work on it productively

### Key Points
- Different database systems optimize for different workloads
- Important to understand trade-offs when choosing technologies
- Highlighted concept: "There is no one-size-fits-all solution" (p. 17)

### Concepts to Process
- [ ] #toprocess Load parameters (p. 11)
- [ ] #toprocess Percentiles in performance (p. 14)
- [ ] #toprocess Evolvability in system design (p. 21)
```

**Resulting Permanent Note:**
`05 - Permanent/20230617-1015 Percentiles in Performance Measurement.md`

```markdown
# 20230617-1015 Percentiles in Performance Measurement

Performance metrics based on averages can be misleading because they hide outliers that affect user experience. Percentiles provide a better picture of real-world performance.

## Key Concepts
- **p50** (median): Normal case performance
- **p95**: The long tail starts to show
- **p99**: The worst 1% of cases
- **p999**: The extreme outliers

## Applications
- SLA definitions should use percentiles, not averages
- Monitoring should track percentiles over time
- Optimization should target specific percentiles based on business needs

## Example Calculation

def percentile(values, p):
    """Calculate the pth percentile of values"""
    # Implementation...

## Related Notes
- [[20230520-1145 Latency vs Throughput]]
- [[20230301-0930 Monitoring System Design]]
- [[SLA Definition Best Practices]]

## Source
- [[Book: Designing Data-Intensive Applications]], p. 14-15
```

**Update to Related MOC:**
`00 - Maps of Content/System Performance MOC.md`

## 5. Technical Problem Solving Flow

### Debugging and Solution Workflow

1. When encountering a problem:
   - Document the issue in your Daily Note (07 - Daily)
   - Include error messages, environment details
   - Track approaches tried

2. When finding the solution:
   - Document the solution in the same note
   - Tag with #solution

3. During weekly processing:
   - If it's a common problem, create a permanent note (05 - Permanent)
   - If it's project-specific, move to project notes (02 - Projects)
   - Link to related concepts

**Example Problem Documentation in Daily Note:**
`07 - Daily/2023-06-18.md`

```markdown
### Docker Container Connection Issue (2:15pm)
Problem: Containers can't connect to each other by service name
Error: `Could not resolve host: auth-service`
Environment: Docker Compose, Ubuntu 22.04

Tried:
- Checked network config in docker-compose.yml ✓
- Verified DNS settings ✓
- Restarted Docker daemon ✓

Solution: Network definition was missing in compose file. Added:

networks:
  app-network:
    driver: bridge

And added network references to each service.
#solution #docker
```

**Resulting Permanent Note:**
`05 - Permanent/20230618-1630 Docker Compose Networking Fundamentals.md`

```markdown
# 20230618-1630 Docker Compose Networking Fundamentals

Docker Compose service-to-service communication requires properly configured networks to enable DNS resolution by service name.

## Common Issues
- Services unable to resolve each other by name
- Connection refused errors between services
- Intermittent connectivity between containers

## Networking Essentials
- Each Compose file needs explicit network definition
- Services must reference the same network
- Bridge driver is standard for single-host deployments
- Container names become DNS entries within the network

## Example Configuration

networks:
  app-network:
    driver: bridge

services:
  service1:
    # service config
    networks:
      - app-network
      
  service2:
    # service config
    networks:
      - app-network

## Debugging Approaches
- Use `docker network ls` to verify network creation
- Check service with `docker-compose ps`
- Test resolution with `docker exec <container> ping <service>`
- Verify network assignment with `docker network inspect`

## Related Notes
- [[20230401-1545 Docker Compose Environment Variables]]
- [[20230225-0915 Container Orchestration Patterns]]
- [[Docker Multi-stage Build Optimization]]

## References
- [[Docker Documentation - Networking]]
```

**Project-Specific Implementation (if applicable):**
`02 - Projects/E-commerce API Modernization/Docker Configuration.md`

## 6. Weekly Review Workflow (Practical Process)

**Schedule on Calendar:**
Friday, 3:00-4:00 PM - "Second Brain Weekly Review"

1. Block 30-60 minutes on calendar (e.g., Friday afternoon)
2. Process inbox notes (from 01 - Inbox)
   - Move to appropriate folders
   - Tag for future reference

3. Review all daily notes from the week (07 - Daily)
   - Extract valuable insights to permanent notes (05 - Permanent)
   - Move project-specific notes to project folders (02 - Projects)
   - Identify recurring themes or problems

4. Update project notes (02 - Projects)
   - Add progress updates
   - Update task lists
   - Document decisions made
   
5. Process fleeting notes (06 - Fleeting)
   - Turn important ones into permanent notes (05 - Permanent)
   - Link to existing concepts
   - Discard if no longer relevant

6. Update relevant MOCs (00 - Maps of Content)
   - Add new permanent notes to appropriate MOCs
   - Create new MOCs if needed for emerging themes

7. Plan next week
   - Review upcoming project milestones
   - Set focus areas for next week
   - Schedule dedicated learning time if needed

**Weekly Review Template Location:**
`99 - Meta/00 - Templates/(TEMPLATE) Weekly Review.md`

**Weekly Review Note:**
`07 - Daily/Review - 2023-W24.md`

These workflows provide concrete examples of how to use your second brain in practice. Start with what feels most natural to you, and gradually incorporate more elements as the system becomes part of your routine. 