# Challenge 1 Part 3: Technical Design Document — Business Monetization Evolution

**Student Name**: [Your Name]
**Submission Date**: [Date]
**Challenge**: ChefConnect Social Recipe Platform — Part 3: Live Cooking Sessions

---

## ⚠️ IMPORTANT: Technology-Agnostic Design Required

Use **building block names** throughout (Service, Worker, Key-Value Store, File Store, Queue, Relational Database, Vector Database). Do **not** name specific technologies (PostgreSQL, Redis, AWS, RTMP, WebRTC, HLS, etc.) in your design decisions. Naming a tool earns automatic point deductions. The whole point of Part 3 is that you can reason about live video as a *pattern* without locking into a vendor.

## 📝 RECOMMENDED APPROACH: Draw First, Write Second

Before you fill this template in, sketch your evolved architecture using the Google Drawing template linked on the challenge page. Drag the 7 building blocks onto the canvas and draw the flows for each piece of the new requirement separately. Then write your decisions here. The diagram surfaces the parallelism that prose hides.

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

## Innovation Context

*ChefConnect now serves 3 million users with excellent performance. The platform is stable. Market research shows huge demand for live cooking experiences. Your job in Part 3 is to add live cooking sessions without breaking the platform Part 2 just stabilized.*

**Primary Focus**: Add Requirement 7 (Live Cooking Sessions) on top of Parts 1-2. Chefs broadcast live video. Followers watch with sub-100ms chat latency. Up to 5,000 concurrent viewers per chef. Sessions auto-save for later viewing. Chefs schedule weekly sessions. The whole thing integrates seamlessly with existing recipes and profiles.

---

## Architecture Overview

**High-Level Description**:
[Describe how your Part 2 design evolves to add live cooking. What is the core idea of your approach? One paragraph.]

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

## Requirements 1-6: Maintaining Platform Stability (40% of Grade)

### Stability Preservation Analysis

**Performance maintained**: [How you keep Part 2's sub-1-second recipe loads and sub-500ms search intact while a chef broadcasts to 5,000 viewers.]

**Core features protected**: [How recipe management, social, search, and profiles keep working while live sessions run alongside them.]

**Resource allocation**: [How you keep heavy live-session traffic from starving the rest of the platform.]

### Integration Impact Assessment

**Recipe Management (Req 1)**: [How live sessions relate to existing recipes, and what (if anything) changes on the recipe path.]

**Social Features (Req 2)**: [How follow relationships interact with live sessions, and what that means for the existing social data.]

**Discovery & Search (Req 3)**: [How a chef being live shows up in search and discovery without slowing the search path.]

**User Profiles (Req 4)**: [How a chef profile reflects live and upcoming sessions while the Part 2 profile performance work stays correct.]

**Content Performance (Req 5)**: [How recipe page loads stay fast even when a heavy live session is happening.]

**High-Performance Optimization (Req 6)**: [How Part 2's scaling decisions still hold once live sessions are added.]

---

## Requirement 7: LIVE COOKING SESSIONS (60% of Grade)

*Chefs broadcast high-quality live video. Followers watch live with sub-100ms chat. Up to 5,000 concurrent viewers per chef. Sessions auto-save for later viewing. Chefs schedule weekly sessions. Seamless integration with existing recipe and profile systems.*

### Live Streaming Architecture

**Purpose**: Document how the live video itself flows from chef to viewer using building block terminology (see the flow notation section above). Show the chef's broadcast path and the viewer's playback path as separate flows.

**Your Live Streaming Flows**:
[Write 3-5 flows covering broadcast start, viewer join, mid-stream state, and broadcast end.]

### Real-Time Chat Architecture

**Purpose**: Document how chat messages reach all viewers in under 100 ms using building block terminology.

**Your Chat Flows**:
[Write 3-5 flows covering send, receive, presence, and moderation. Be explicit about where chat messages live at each point in their lifecycle.]

### Recording & Playback Architecture

**Purpose**: Document how a live session becomes a permanent, watchable recording.

**Your Recording Flows**:
[Write 2-4 flows covering capture, post-session processing, and later viewing including chat replay.]

### Scheduling Integration

**Purpose**: Document how a chef schedules a weekly session and how followers find out about it.

**Your Scheduling Flows**:
[Write 2-4 flows covering creating a schedule, weekly recurrence, follower notifications, and the moment a scheduled session opens.]

### User Flow Design

**Purpose**: Tie the four pieces above together as user-facing journeys.

**Your User Journeys**:
[Write 3-5 end-to-end journeys that show how the four sub-architectures cooperate.]

### Architecture Decisions & Trade-offs

**Live video delivery**: [Which building blocks and entities carry the video from one chef to 5,000 viewers, and why. What alternative you rejected and what trade-off you accepted.]

**Chat at sub-100ms**: [Which building blocks deliver the chat latency target and why. What latency you actually expect, and why your combination hits 100 ms. Be prepared to defend why the patterns you used elsewhere do or do not apply here.]

**Recording pipeline**: [How a finished session becomes a watchable recording without blocking anything user-facing. What guarantees you give about when a recording is available.]

**Scheduling and notifications**: [Which building blocks and entities drive weekly scheduling, and why.]

**Integration vs. isolation**: [How tightly the live-session components couple to the existing recipe/profile components. What you decoupled deliberately to keep failures contained.]

**What you considered and rejected**: [At least one trade-off. Show that you weighed alternatives.]

### Technical Implementation Details

**Per-block live-session role**:
[For each building block and external entity in your live-session design, describe the job it does, what data or work it owns, and any lifecycle considerations.]

---

## Overall Architecture Analysis

### Innovation Strategy

[The thesis of your evolution. One paragraph explaining how you added a real-time, video-heavy feature on top of a stable platform without rewriting it.]

### Building Block Evolution from Part 2

[For each block in your Part 2 design, what changed in Part 3. Bullet list is fine.]

### Live Streaming Performance Targets

[Quantitative claims tied to the requirements. Sub-100ms chat. 5,000 concurrent viewers per chef. Recording available within X minutes of session end. Notification arrival window. Tie each number to which building blocks deliver it.]

### Trade-offs Made

[At least three trade-offs you accepted. Write each as "We accepted X cost in order to gain Y benefit." At least one should be about live vs. recorded experience. At least one should be about cost (live video is expensive).]

### Innovation Success Metrics

[How you would measure that the live cooking feature actually worked. SLOs. Engagement metrics. Recording availability. Chat latency p95. Concurrent-viewer ceiling without degradation.]

---

## Submission Checklist

Before submitting, verify:

- [ ] Every architecture decision uses **building block names**, not technology names.
- [ ] All 6 prior requirements are still addressed and still working.
- [ ] All 7 sub-bullets of Requirement 7 are covered: high-quality live video, sub-100ms chat, 5,000 concurrent viewers, auto-saved recordings, weekly scheduling, recipe integration, profile integration.
- [ ] Every building block and entity you added has a clear, stated reason.
- [ ] At least three trade-offs are explicitly named.
- [ ] User flows are documented with building block terminology, separated into the distinct planes of the live-session problem.
- [ ] You can explain *why* each evolution decision was made, not just *what* changed.
