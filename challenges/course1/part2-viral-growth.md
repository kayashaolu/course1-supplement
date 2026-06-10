# Challenge 1 Part 2: Technical Design Document — Viral Growth Evolution

**Student Name**: [Your Name]
**Submission Date**: [Date]
**Challenge**: ChefConnect Social Recipe Platform — Part 2: Viral Growth Evolution

---

## ⚠️ IMPORTANT: Technology-Agnostic Design Required

Use **building block names** throughout (Service, Worker, Key-Value Store, File Store, Queue, Relational Database, Vector Database). Do **not** name specific technologies (PostgreSQL, Redis, AWS, etc.) in your design decisions. Naming a tool earns automatic point deductions; the goal of this challenge is to develop pattern thinking that is durable across the AI era's tool churn.

## 📝 RECOMMENDED APPROACH: Draw First, Write Second

Before you fill this template in, sketch your evolved architecture using the Google Drawing template linked on the challenge page. Drag the 7 building blocks onto the canvas, draw the data flows, and only *then* write your decisions here. The diagram surfaces design pressure that prose hides.

## ✏️ Flow Notation: How to Write User Flows

Every flow in this document uses building-block notation. Here is the format, illustrated with a system this course does not cover — a city library's book-reservation system:

```
Reserve a book: User → Reservation Service → Relational Database (availability check) → Queue → Notification Worker → External Service (SMS)
Browse the catalog: User → Catalog Service + Key-Value Store → Relational Database (on cache miss)
```

- Use EXACT building block names: Service, Worker, Queue, Key-Value Store, File Store, Relational Database, Vector Database, User, External Service, Time
- Use the `+` symbol for building block combinations (e.g., Queue + Worker)
- Annotate a step's purpose in parentheses when it is not obvious

Your flows should look like this in notation — the architecture is yours to design.

---

## Crisis Context

*ChefConnect went viral. Daily active users jumped from 10,000 to 2 million in 3 months. The platform is breaking under load: recipe pages load in 4–6 seconds (target <1s), search times out during peak traffic (target <500ms), image uploads fail with 10,000+ concurrent uploads, and user satisfaction has dropped 15% week-over-week.*

**Primary Focus**: Evolve the Part 1 architecture to handle 2M+ users with sub-1-second recipe page loads and sub-500ms search. **NO new features during this crisis** — the scope is performance and scaling improvements only. The system must be ready to scale to 5M users within 6 months.

---

## Architecture Overview

**High-Level Description**:
[Describe how your Part 1 design evolves to absorb 200x user growth. What is the core idea of your scaling approach? One paragraph.]

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

## Requirements 1–5: Maintaining Core Functionality (40% of Grade)

### Continuity Analysis

**What stayed the same**: [Which parts of your Part 1 design remain unchanged.]

**What had to change**: [Which parts needed modification to absorb scale.]

**Breaking changes avoided**: [How you maintained backward compatibility with existing user flows and data.]

### Performance Impact Assessment

**Recipe Management (Req 1)**: [How 200x user growth affects recipe CRUD operations. Demonstrates that Part 1 features still work under load.]

**Social Features (Req 2)**: [How viral growth impacts following, likes, and comments. Shows evolution of social features without breaking them.]

**Discovery & Search (Req 3)**: [How increased content volume and query rates affect search performance. Maintains existing search semantics while scaling throughput.]

**User Profiles (Req 4)**: [How growth affects profile loading and follower-count display. Preserves profile functionality under load.]

**Content Performance (Req 5)**: [How the traffic spike forces evolution of the original performance strategy.]

---

## Requirement 6: HIGH-PERFORMANCE OPTIMIZATION (60% of Grade)

*Recipe pages load in under 1 second for 2M+ users. Search results return in under 500ms during peak traffic. Handle 10,000+ concurrent image uploads. System ready to scale to 5M users within 6 months. **NO new features during the crisis.***

### Crisis Analysis

**Primary Bottlenecks Identified**:
1. **[Bottleneck 1]**: [What is breaking, why, and which Part 1 building block is under pressure.]
2. **[Bottleneck 2]**: [Same.]
3. **[Bottleneck 3]**: [Same.]

### User Flow Optimization

**Purpose**: Document performance-optimized user flows using building block terminology (see the flow notation section above).

**Optimized Flows**:

[For each major user flow that was slow, write the new path through your blocks, noting the current latency and the target.]

### Architecture Decisions & Trade-offs

**[Scaling decision 1]**: [Name the bottleneck it addresses, the building block change you are making, and why it works. Name the *pattern*, not a tool.]

**[Scaling decision 2]**: [Same.]

**[Scaling decision 3]**: [Same.]

**What you considered and rejected**: [At least one trade-off. Show that you weighed alternatives.]

### Technical Implementation Details

**Per-block load handling**:
[For each building block in your evolved design, describe how it behaves under 2M-user load: what pressure it absorbs, what changes from Part 1, and what its failure or overflow behavior is.]

---

## Overall Architecture Analysis

### Crisis Response Strategy

[The thesis of your evolution. One paragraph explaining your approach to going from 10K to 2M users without rebuilding from scratch.]

### Building Block Evolution from Part 1

[For each block in your Part 1 design, what changed in Part 2. Bullet list is fine.]

### Crisis Optimization Results

[Quantitative claims about what your evolved design achieves. Page load latency, search latency, concurrent upload capacity, headroom for 5M users. Tie back to the requirements.]

### Trade-offs Made

[At least three trade-offs you accepted. Write each as "We accepted X cost in order to gain Y benefit."]

### Crisis Management Success Metrics

[How you would measure that the crisis response worked. SLOs you would commit to.]

---

## Submission Checklist

Before submitting, verify:

- [ ] Every architecture decision uses **building block names**, not technology names.
- [ ] All 5 original requirements are still addressed and still working.
- [ ] Requirement 6 is fully addressed with concrete optimization decisions.
- [ ] No new features added during the crisis (this lowers the score).
- [ ] At least three trade-offs are explicitly named.
- [ ] User flows are documented with building block terminology.
- [ ] You can explain *why* each evolution decision was made, not just *what* changed.
