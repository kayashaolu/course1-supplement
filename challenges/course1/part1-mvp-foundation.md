# Challenge 1 Part 1: Technical Design Document - MVP Foundation

**Student Name**: [Your Name]  
**Submission Date**: [Date]  
**Challenge**: ChefConnect Social Recipe Platform - Part 1 MVP Foundation

---

## ⚠️ IMPORTANT: Technology-Agnostic Design Required

This technical design document must focus on **building blocks and architectural patterns**, not specific technologies. 

**✅ DO USE:**
- Building block names: Service, Worker, Queue, Key-Value Store, File Store, Relational Database, Vector Database
- Technology-agnostic terms that describe patterns (e.g., cache, indexes, async processing)

**❌ DO NOT USE:**
- Specific technologies: PostgreSQL, MongoDB, MySQL, Redis, Elasticsearch, RabbitMQ, Kafka, etc.
- Vendor names: AWS, Google Cloud, Azure, Docker, Kubernetes, etc.
- Programming languages or frameworks: Node.js, Python, React, etc.

Remember: Senior engineers think in patterns that transcend specific technologies!

## 📝 RECOMMENDED APPROACH: Draw First, Write Second

**Before completing this document:**
1. **Draw your architecture diagram** using the 7 building blocks + 3 external entities - use [this template](https://docs.google.com/drawings/d/1hbx9r8NCBNjMDZv9tAXzfvLR3-XPsOgHm9zrX0h_cO8/edit?usp=sharing) to get started
2. **Use your diagram as reference** while writing your user flows and technical explanations
3. **Ensure consistency** between what you draw and what you write

This approach helps you think systematically and creates more accurate technical descriptions.

## ✏️ Flow Notation: How to Write User Flows

Every flow in this document uses building-block notation. Here is the format, illustrated with a system this course does not cover — a city library's book-reservation system:

```
Reserve a book: User → Reservation Service → Relational Database (availability check) → Queue → Notification Worker → External Service (SMS)
Browse the catalog: User → Catalog Service + Key-Value Store → Relational Database (on cache miss)
```

- Use EXACT building block names: Service, Worker, Queue, Key-Value Store, File Store, Relational Database, Vector Database, User, External Service, Time
- Use the `+` symbol for building block combinations (e.g., Queue + Worker)
- Start flows with the external entity that triggers them
- Annotate a step's purpose in parentheses when it is not obvious

Your flows should look like this in notation — the architecture is yours to design.

---

## Architecture Overview

**High-Level Description**: 
[Provide a 2-3 sentence overview of your overall architecture approach for the MVP]

**Core Building Blocks Used**:
- [ ] Service (Blue Rectangle)
- [ ] Worker (Blue Trapezoid)  
- [ ] Key-Value Store (Pink Diamond)
- [ ] File Store (Pink Pentagon)
- [ ] Queue (Pink Stacked Rectangles)
- [ ] Relational Database (Pink Cylinder)
- [ ] Vector Database (Pink Cube)
- [ ] User (Green Smiley)
- [ ] External Service (Green Cloud)
- [ ] Time (Green Hourglass)

---

## Requirement 1: Recipe Management
*Users can create, edit, and organize recipes with ingredients, instructions, photos, and cooking metadata (prep time, difficulty, servings)*

### User Flow Design
**Purpose**: Document the exact paths users take through your system using building block terminology (see the flow notation section above).

**Your Recipe Management Flows:**
[Write 3-5 specific flows for recipe management using building block names]

### Architecture Decisions & Trade-offs
**Purpose**: Explain your building block choices and the trade-offs you considered.

**Key Architectural Decisions:**
- **[Decision 1]**: [Why you chose this building block combination over alternatives]
- **[Decision 2]**: [What trade-offs you made (performance vs complexity, cost vs features, etc.)]
- **[Decision 3]**: [How your choices specifically address recipe management challenges]

### Technical Implementation Details
**Purpose**: Describe the specific technical mechanisms within your building blocks.

**Data Organization**: [How you structure recipe data within your chosen storage building blocks]

**Processing Logic**: [How your Service building blocks handle recipe operations]

**Performance Mechanisms**: [Specific techniques for fast recipe access]

---

## Requirement 2: Social Features
*Users can follow chefs, like recipes, leave comments, and share recipes with friends outside the platform*

### User Flow Design
**Purpose**: Document the exact paths users take for social interactions using building block terminology.

**Your Social Feature Flows:**
[Write 3-5 specific flows for social interactions using building block names]

### Architecture Decisions & Trade-offs
**Purpose**: Explain your social feature architecture choices and trade-offs.

**Key Architectural Decisions:**
- **[Decision 1]**: [Why you chose specific building blocks for social data vs alternatives]
- **[Decision 2]**: [Trade-offs you weighed for how social actions are processed]
- **[Decision 3]**: [How you balance social feature performance with data consistency]

### Technical Implementation Details
**Purpose**: Describe the specific mechanisms for social feature processing.

**Social Data Organization**: [How you structure followers, likes, comments within storage building blocks]

**Interaction Processing**: [How your building blocks handle different types of social actions]

**Notification Strategy**: [How notifications reach users, and what that means for the user who triggered them]

---

## Requirement 3: Discovery & Search
*Users can search recipes by ingredients, cuisine type, dietary restrictions, and difficulty level with fast results*

### User Flow Design
**Purpose**: Document search and discovery paths using building block terminology.

**Your Discovery & Search Flows:**
[Write 3-5 specific flows for search and discovery using building block names]

### Architecture Decisions & Trade-offs
**Purpose**: Explain your search architecture choices and performance trade-offs.

**Key Architectural Decisions:**
- **[Decision 1]**: [Why you chose specific building blocks for search vs alternatives]
- **[Decision 2]**: [Trade-offs between search accuracy and speed]
- **[Decision 3]**: [How you handle different search complexity levels]

### Technical Implementation Details
**Purpose**: Describe search mechanisms within your building blocks.

**Search Data Organization**: [How you structure searchable data within storage building blocks]

**Query Processing**: [How your Service building blocks handle different search types]

**Performance Optimization**: [Specific techniques for fast search]

---

## Requirement 4: User Profiles
*Chefs have detailed profiles showcasing their specialties, follower counts, popular recipes, and personal cooking story*

### User Flow Design
**Purpose**: Document profile interaction paths using building block terminology.

**Your User Profile Flows:**
[Write 3-5 specific flows for profile interactions using building block names]

### Architecture Decisions & Trade-offs
**Purpose**: Explain profile architecture choices and data consistency trade-offs.

**Key Architectural Decisions:**
- **[Decision 1]**: [Why you chose specific building blocks for profile data vs alternatives]
- **[Decision 2]**: [Trade-offs you weighed for serving profile statistics]
- **[Decision 3]**: [How you handle profile completeness and social proof]

### Technical Implementation Details
**Purpose**: Describe profile data processing mechanisms.

**Profile Data Organization**: [How you structure profile information within storage building blocks]

**Metrics Calculation**: [How you compute and update social metrics efficiently]

**Content Assembly**: [How you combine profile data with recipes and social information]

---

## Requirement 5: Content Performance
*Platform must load recipe pages quickly, handle image uploads efficiently, and provide smooth browsing experience for food content discovery*

### User Flow Design
**Purpose**: Document performance-optimized paths using building block terminology.

**Your Performance-Optimized Flows:**
[Write 3-5 specific flows showing performance optimizations using building block names]

### Architecture Decisions & Trade-offs
**Purpose**: Explain performance architecture choices and optimization trade-offs.

**Key Architectural Decisions:**
- **[Decision 1]**: [Why you chose specific building block combinations for performance]
- **[Decision 2]**: [Trade-offs between consistency and speed]
- **[Decision 3]**: [How you prioritize user experience vs system efficiency]

### Technical Implementation Details
**Purpose**: Describe specific performance mechanisms within building blocks.

**Page Load Strategy**: [How your building blocks keep recipe pages fast]

**Upload Handling Strategy**: [How your building blocks keep uploads reliable under load]

**Content Delivery**: [How your building blocks work together for fast media delivery]

---

## Overall Architecture Analysis

### Key Design Decisions
1. **[Decision 1]**: [Rationale for this architectural choice]
2. **[Decision 2]**: [Rationale for this architectural choice]
3. **[Decision 3]**: [Rationale for this architectural choice]

### Building Block Combinations Used
- **[Pattern 1]**: [Building blocks combined and why]
- **[Pattern 2]**: [Building blocks combined and why]
- **[Pattern 3]**: [Building blocks combined and why]

### Trade-offs Made
**Performance vs Complexity**: [What trade-offs you made]

**Cost vs Features**: [What trade-offs you made]

**Scalability vs Simplicity**: [What trade-offs you made for MVP]

### Potential Improvements
[What you would add/change if you had more time or resources]

---

## Submission Checklist
- [ ] All 5 requirements addressed with complete user flows
- [ ] Building blocks properly labeled in diagram
- [ ] All building blocks connected (no floating components)
- [ ] Flows written in the notation shown at the top of this document
- [ ] Technical justifications provided for each requirement
- [ ] Trade-offs and design decisions clearly explained
