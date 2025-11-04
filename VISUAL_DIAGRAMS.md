# Visual Diagrams: Ambient Code Platform UX Architecture

**Purpose**: Visual representations of key UX concepts and structures
**Version**: 1.0
**Date**: 2025-11-04

---

## Table of Contents
1. [Ecosystem Positioning](#ecosystem-positioning)
2. [Information Architecture](#information-architecture)
3. [User Journey Flows](#user-journey-flows)
4. [Component Hierarchy](#component-hierarchy)
5. [Navigation System](#navigation-system)
6. [State Management](#state-management)
7. [Real-time Data Flow](#real-time-data-flow)

---

## Ecosystem Positioning

### AI Development Tool Landscape

```
┌─────────────────────────────────────────────────────────────────┐
│                  AI DEVELOPMENT ECOSYSTEM                        │
└─────────────────────────────────────────────────────────────────┘

┌──────────────┐        ┌─────────────────┐        ┌──────────────┐
│ Code Editors │        │ Ambient Code    │        │ ML Platforms │
│              │        │ Platform        │        │              │
│ • VS Code    │        │                 │        │ • Vertex AI  │
│ • JetBrains  │◄──────►│ AI Agent        │◄──────►│ • SageMaker  │
│ • Cursor     │        │ Orchestration   │        │ • Azure ML   │
│              │        │                 │        │              │
└──────────────┘        └─────────────────┘        └──────────────┘
       ▲                        ▲                          ▲
       │                        │                          │
       │                        │                          │
       ▼                        ▼                          ▼
┌──────────────┐        ┌─────────────────┐        ┌──────────────┐
│ DevOps Tools │        │   Kubernetes    │        │  Monitoring  │
│              │        │                 │        │              │
│ • GitHub     │◄──────►│ Orchestration   │◄──────►│ • Datadog    │
│ • GitLab     │        │ Layer           │        │ • Grafana    │
│ • Jenkins    │        │                 │        │ • Prometheus │
└──────────────┘        └─────────────────┘        └──────────────┘

Legend:
◄──────► Integration/Data Flow
We sit at the center: orchestrating AI agents on Kubernetes infrastructure
```

---

## Information Architecture

### Hub-and-Spoke Model

```
                        ┌───────────────┐
                        │   DASHBOARD   │
                        │   (Hub/Home)  │
                        └───────┬───────┘
                                │
                ┌───────────────┼───────────────┐
                │               │               │
                ▼               ▼               ▼
        ┌───────────┐   ┌───────────┐   ┌───────────┐
        │ PROJECTS  │   │ SESSIONS  │   │ ANALYTICS │
        └─────┬─────┘   └─────┬─────┘   └─────┬─────┘
              │               │               │
        ┌─────┴─────┐   ┌─────┴──────┐  ┌─────┴─────┐
        │           │   │            │  │           │
        ▼           ▼   ▼            ▼  ▼           ▼
    Templates  History  Agents   Logs   Metrics  Reports
                        Artifacts
```

### Site Map (Detailed)

```
Ambient Code Platform
│
├── Dashboard
│   ├── Overview (default)
│   ├── Recent Activity
│   └── Quick Actions
│
├── Projects
│   ├── All Projects
│   ├── Project Detail
│   │   ├── Overview
│   │   ├── Sessions
│   │   ├── Configuration
│   │   ├── Team Access
│   │   └── History
│   ├── Templates
│   │   ├── Browse
│   │   ├── Template Detail
│   │   ├── My Templates
│   │   └── Create Template
│   └── Create New
│
├── Sessions
│   ├── Active Sessions
│   ├── Session History
│   ├── Session Detail
│   │   ├── Overview (default)
│   │   ├── Agents
│   │   │   └── Agent Detail
│   │   │       ├── Activity
│   │   │       ├── Reasoning
│   │   │       ├── Logs
│   │   │       └── Configuration
│   │   ├── Logs (unified)
│   │   ├── Artifacts
│   │   ├── Metrics
│   │   └── Actions
│   └── Create New
│
├── Analytics
│   ├── Business Metrics
│   ├── Adoption & Usage
│   ├── Performance
│   └── Reports
│       ├── Pre-built
│       ├── Custom Builder
│       └── Scheduled
│
└── Settings
    ├── Profile
    ├── Integrations
    │   ├── Connected Accounts
    │   ├── API & Webhooks
    │   └── Observability
    ├── AI Models
    ├── Resources
    ├── Team (if applicable)
    └── Platform
```

---

## User Journey Flows

### Journey 1: First Session Creation

```
START
  │
  ▼
┌─────────────────┐
│ Land on         │  Emotion: 😊 Curious
│ Dashboard       │  Time: 0-2 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Browse          │  Emotion: 🤔 Uncertain
│ Templates       │  Time: 2-5 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Configure       │  Emotion: 😰 Anxious
│ Session         │  Time: 5-15 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Monitor         │  Emotion: 😌 Relieved
│ Execution       │  Time: 15-25 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Review          │  Emotion: 😄 Satisfied
│ Results         │  Time: 25-30 min
└────────┬────────┘
         │
         ▼
        END

Critical Moments:
━━━━━━━━━━━━━━━
⚡ First 30 seconds → Must establish value
⚡ Template selection → Must build confidence
⚡ First agent action → Must show transparency
⚡ Session completion → Must prove value
```

### Journey 2: Error Recovery

```
START (Alert Received)
  │
  ▼
┌─────────────────┐
│ Triage          │  Emotion: 😐 Focused
│ Error           │  Time: 0-3 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Diagnose        │  Emotion: 😟 Concerned
│ Root Cause      │  Time: 3-8 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Deep Dive       │  Emotion: 😤 Frustrated
│ Reasoning/Logs  │  Time: 8-15 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Apply Fix       │  Emotion: 🤔 Analytical
│ & Test          │  Time: 15-20 min
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Validate        │  Emotion: 😌 Resolved
│ Resolution      │  Time: 20-25 min
└────────┬────────┘
         │
         ▼
        END

Success Factors:
━━━━━━━━━━━━━━━
✓ 3-second error assessment
✓ Self-service resolution >60%
✓ Clear root cause identification
✓ Confident intervention capability
```

---

## Component Hierarchy

### Atomic Design Structure

```
┌─────────────────────────────────────────────────────────────┐
│ PAGES (Routes)                                              │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ TEMPLATES (Page Layouts)                                │ │
│ │ ┌─────────────────────────────────────────────────────┐ │ │
│ │ │ ORGANISMS (Complex Components)                      │ │ │
│ │ │ ┌─────────────────────────────────────────────────┐ │ │ │
│ │ │ │ MOLECULES (Composite Components)                │ │ │ │
│ │ │ │ ┌─────────────────────────────────────────────┐ │ │ │ │
│ │ │ │ │ ATOMS (Basic UI Elements)                   │ │ │ │ │
│ │ │ │ │                                             │ │ │ │ │
│ │ │ │ │ • Button                                    │ │ │ │ │
│ │ │ │ │ • Input                                     │ │ │ │ │
│ │ │ │ │ • Badge                                     │ │ │ │ │
│ │ │ │ │ • Icon                                      │ │ │ │ │
│ │ │ │ └─────────────────────────────────────────────┘ │ │ │ │
│ │ │ │                                                   │ │ │ │
│ │ │ │ • SearchBar (Input + Icon + Button)             │ │ │ │
│ │ │ │ • StatusBadge (Badge + Icon + Text)             │ │ │ │
│ │ │ │ • TimestampDisplay (Text + Tooltip)             │ │ │ │
│ │ │ └─────────────────────────────────────────────────┘ │ │ │
│ │ │                                                       │ │ │
│ │ │ • AgentActivityFeed (Cards + Timeline)              │ │ │
│ │ │ • SessionCard (Header + Status + Actions)           │ │ │
│ │ │ • NavigationSidebar (Menu + Icons + State)          │ │ │
│ │ └─────────────────────────────────────────────────────┘ │ │
│ │                                                           │ │
│ │ • SessionDetailTemplate (Header + Tabs + Content)       │ │
│ │ • DashboardTemplate (Grid + Cards + Feed)               │ │
│ └─────────────────────────────────────────────────────────┘ │
│                                                               │
│ • /dashboard                                                 │
│ • /sessions                                                  │
│ • /sessions/[id]                                             │
└─────────────────────────────────────────────────────────────┘
```

### Key Component Relationships

```
SessionDetailPage
├── PageHeader
│   ├── Breadcrumbs
│   ├── Title (with StatusBadge)
│   └── ActionButtons
│       ├── Button (Clone)
│       ├── Button (Stop)
│       └── DropdownMenu (More)
│
├── TabNavigation
│   ├── Tab (Overview) ← active
│   ├── Tab (Agents)
│   ├── Tab (Logs)
│   ├── Tab (Artifacts)
│   └── Tab (Metrics)
│
└── ContentArea
    ├── MainContent (70%)
    │   └── AgentActivityFeed
    │       ├── AgentCard (Planning Agent)
    │       │   ├── AgentHeader
    │       │   ├── ActivityTimeline
    │       │   └── AgentActions
    │       ├── AgentCard (Code Agent)
    │       └── AgentCard (Test Agent)
    │
    └── Sidebar (30%)
        ├── MetadataCard
        ├── QuickStatsCard
        └── RelatedItemsCard
```

---

## Navigation System

### Global Navigation Structure

```
┌────────────────────────────────────────────────────────────────┐
│ [Logo]  Dashboard  Projects  Sessions  Analytics   [🔍] [🔔] [⚙]│
└────────────────────────────────────────────────────────────────┘
│ Home > Sessions > API Deploy #42                               │
├──────────────┬─────────────────────────────────────────────────┤
│ Sidebar      │ Content Area                                    │
│              │                                                 │
│ Overview     │ ┌─────────────────────────────────────────────┐│
│ Agents       │ │                                             ││
│  • Planning  │ │                                             ││
│  • Code      │ │        Main Content                         ││
│  • Test      │ │                                             ││
│ Logs         │ │                                             ││
│ Artifacts    │ │                                             ││
│ Metrics      │ └─────────────────────────────────────────────┘│
│ Actions      │                                                 │
│              │                                                 │
│ ──────────── │                                                 │
│ ← Back       │                                                 │
└──────────────┴─────────────────────────────────────────────────┘

Legend:
━━━━━━
Top Bar:    Always visible, global navigation
Breadcrumbs: Context and navigation trail
Sidebar:    Contextual navigation (collapsible)
Content:    Main workspace area
```

### Navigation Hierarchy

```
Level 1: Global (Top Navigation)
├── Dashboard
├── Projects
├── Sessions
├── Analytics
└── Settings

Level 2: Section (Sidebar or Tabs)
├── Dashboard
│   ├── Overview
│   ├── Recent Activity
│   └── Quick Actions
├── Sessions
│   ├── Active
│   ├── History
│   └── Create New
└── Session Detail
    ├── Overview
    ├── Agents
    ├── Logs
    ├── Artifacts
    └── Metrics

Level 3: Content (Main Area)
└── Session Detail > Agents
    ├── Agent List
    └── Agent Detail
        ├── Activity
        ├── Reasoning
        ├── Logs
        └── Configuration

Max Depth: 4 levels before modal/overlay
Optimal: 3 levels (Global > Section > Content)
```

---

## State Management

### State Architecture

```
┌─────────────────────────────────────────────────────────────┐
│ APPLICATION STATE                                           │
└─────────────────────────────────────────────────────────────┘

┌──────────────────────┐          ┌──────────────────────────┐
│ Server State         │          │ UI State                 │
│ (React Query)        │          │ (Zustand)                │
├──────────────────────┤          ├──────────────────────────┤
│                      │          │                          │
│ • Sessions           │          │ • Sidebar collapsed      │
│ • Projects           │          │ • Active tab             │
│ • Agents             │          │ • Modal open             │
│ • Logs               │          │ • Filters applied        │
│ • Artifacts          │          │ • Dark mode              │
│ • Analytics          │          │ • Notifications          │
│                      │          │                          │
│ Features:            │          │ Features:                │
│ • Automatic caching  │          │ • Lightweight            │
│ • Background refresh │          │ • Persist to localStorage│
│ • Optimistic updates │          │ • Simple API             │
│ • Invalidation       │          │ • No boilerplate         │
└──────────────────────┘          └──────────────────────────┘
         ▲                                    ▲
         │                                    │
         └────────────────┬───────────────────┘
                          │
                          ▼
                 ┌────────────────┐
                 │ React          │
                 │ Components     │
                 └────────────────┘
```

### Data Flow Pattern

```
User Action
    │
    ▼
┌────────────────┐
│ Event Handler  │
└───────┬────────┘
        │
        ▼
┌────────────────┐
│ API Call       │ ← React Query mutation
└───────┬────────┘
        │
        ├──────────────────┐
        │                  │
        ▼                  ▼
┌────────────────┐  ┌─────────────────┐
│ Optimistic     │  │ Backend API     │
│ Update (UI)    │  │                 │
└────────────────┘  └────────┬────────┘
                            │
                            ▼
                    ┌─────────────────┐
                    │ Database        │
                    └────────┬────────┘
                            │
                            ▼
                    ┌─────────────────┐
                    │ Response        │
                    └────────┬────────┘
                            │
                            ▼
                    ┌─────────────────┐
                    │ Cache Update    │ ← React Query
                    └────────┬────────┘
                            │
                            ▼
                    ┌─────────────────┐
                    │ UI Re-render    │
                    └─────────────────┘
```

---

## Real-time Data Flow

### WebSocket Communication Pattern

```
┌──────────────┐                              ┌──────────────┐
│   Browser    │                              │   Backend    │
│   (Client)   │                              │   Server     │
└──────┬───────┘                              └──────┬───────┘
       │                                             │
       │ 1. Connect WebSocket                        │
       ├────────────────────────────────────────────►│
       │                                             │
       │ 2. Subscribe to Session                     │
       ├────────────────────────────────────────────►│
       │    { sessionId: "123" }                     │
       │                                             │
       │                                             │
       │◄────────────────────────────────────────────┤
       │ 3. Acknowledge Subscription                 │
       │                                             │
       │                                             │
       │◄────────────────────────────────────────────┤
       │ 4. Agent Status Update                      │
       │    { type: "agent:status",                  │
       │      agentId: "code-agent",                 │
       │      status: "running" }                    │
       │                                             │
       │                                             │
       │◄────────────────────────────────────────────┤
       │ 5. Agent Activity                           │
       │    { type: "agent:activity",                │
       │      agentId: "code-agent",                 │
       │      message: "Analyzing..." }              │
       │                                             │
       │                                             │
       │◄────────────────────────────────────────────┤
       │ 6. Reasoning Update                         │
       │    { type: "agent:reasoning",               │
       │      steps: [...] }                         │
       │                                             │
       │                                             │
       │◄────────────────────────────────────────────┤
       │ 7. Session Complete                         │
       │    { type: "session:complete" }             │
       │                                             │
       │ 8. Disconnect                               │
       ├────────────────────────────────────────────►│
       │                                             │
       ▼                                             ▼

Event Types:
━━━━━━━━━━━━
session:update    - Session status changed
agent:status      - Agent status changed
agent:activity    - Agent performed action
agent:reasoning   - Reasoning step added
agent:error       - Agent encountered error
session:complete  - Session finished
```

### WebSocket + React Query Integration

```
┌─────────────────────────────────────────────────────────────┐
│ React Component                                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  useQuery('session', fetchSession)                          │
│         ↓                                                   │
│  Initial data loaded from API                               │
│         ↓                                                   │
│  Display UI with data                                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
         │                                 ▲
         │ useWebSocket('session:123')    │
         ▼                                 │
┌─────────────────────────────────────────┴───────────────────┐
│ WebSocket Hook                                              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. Connect to WebSocket                                    │
│  2. Subscribe to session updates                            │
│  3. Receive real-time events                                │
│         ↓                                                   │
│  4. Update React Query cache                                │
│     queryClient.setQueryData('session', updatedData)        │
│         ↓                                                   │
│  5. React Query triggers re-render                          │
│                                                             │
└─────────────────────────────────────────────────────────────┘

Benefits:
━━━━━━━━
✓ Initial data from REST API (reliable)
✓ Real-time updates via WebSocket (fast)
✓ Single source of truth (React Query cache)
✓ Automatic UI updates on data changes
✓ Fallback to polling if WebSocket fails
```

---

## Implementation Phases

### Phase Timeline Visualization

```
Week:  1    2    3    4    5    6    7    8    9   10   11   12   13   14   15   16
       └────────────────┴────────────────┴────────────────┴────────────────┘
       Phase 1           Phase 2          Phase 3          Phase 4
       Foundation        Core Features    Advanced         Polish & Scale

Phase 1: Foundation (Weeks 1-4)
┌──────────────────────────────────────────────────────────────┐
│ Week 1: Design System Setup                                  │
│ Week 2: Layout & Navigation                                  │
│ Week 3: Core Patterns                                        │
│ Week 4: Data Display Components                              │
│                                                              │
│ Output: Base component library, navigation shell            │
└──────────────────────────────────────────────────────────────┘

Phase 2: Core Features (Weeks 5-8)
┌──────────────────────────────────────────────────────────────┐
│ Week 5: Session List & Creation                              │
│ Week 6: Session Detail & Monitoring                          │
│ Week 7: Project Management                                   │
│ Week 8: Dashboard & Quick Actions                            │
│                                                              │
│ Output: Functional session and project management           │
└──────────────────────────────────────────────────────────────┘

Phase 3: Advanced Features (Weeks 9-12)
┌──────────────────────────────────────────────────────────────┐
│ Week  9: Reasoning Visibility                                │
│ Week 10: Intervention & Control                              │
│ Week 11: Artifact Management                                 │
│ Week 12: Analytics Dashboard                                 │
│                                                              │
│ Output: AI-specific differentiators, business metrics        │
└──────────────────────────────────────────────────────────────┘

Phase 4: Polish & Scale (Weeks 13-16)
┌──────────────────────────────────────────────────────────────┐
│ Week 13: Performance Optimization                            │
│ Week 14: Advanced Accessibility                              │
│ Week 15: Mobile Optimization                                 │
│ Week 16: Documentation & Launch Prep                         │
│                                                              │
│ Output: Production-ready, optimized, documented platform     │
└──────────────────────────────────────────────────────────────┘
```

---

## Testing Strategy

### Testing Pyramid

```
                    ┌─────────────┐
                   ╱  E2E Tests   ╲      10%
                  ╱  (Playwright)  ╲     ~20 tests
                 ├─────────────────┤
                ╱  Integration     ╲    20%
               ╱  Tests (RTL+MSW)   ╲   ~80 tests
              ├─────────────────────┤
             ╱     Unit Tests       ╲  70%
            ╱   (Jest + RTL)         ╲ ~400 tests
           ╲_________________________╱

Coverage:
────────
Unit Tests:        Functions, hooks, utilities (>80%)
Integration Tests: Components + API mocking
E2E Tests:         Critical user journeys

Accessibility:
─────────────
Automated:  axe-core in every component test
Manual:     Keyboard nav, screen reader testing
Continuous: Every PR must pass accessibility checks
```

### Test Coverage by Layer

```
┌─────────────────────────────────────────────────────────────┐
│ Component Layer                                             │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ Unit Tests (70%)                                        │ │
│ │ • Rendering                                             │ │
│ │ • Props handling                                        │ │
│ │ • User interactions                                     │ │
│ │ • Edge cases                                            │ │
│ └─────────────────────────────────────────────────────────┘ │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ Accessibility Tests (100%)                              │ │
│ │ • axe-core automated                                    │ │
│ │ • Keyboard navigation                                   │ │
│ │ • ARIA labels                                           │ │
│ │ • Color contrast                                        │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ Integration Layer                                           │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ Integration Tests (20%)                                 │ │
│ │ • Component + API interactions                          │ │
│ │ • State management integration                          │ │
│ │ • Multi-component workflows                             │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ E2E Layer                                                   │
│ ┌─────────────────────────────────────────────────────────┐ │
│ │ E2E Tests (10%)                                         │ │
│ │ • Critical user journeys                                │ │
│ │ • Cross-browser testing                                 │ │
│ │ • Performance testing                                   │ │
│ └─────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

---

## Responsive Breakpoints

### Layout Adaptation Strategy

```
Mobile (<768px)
┌──────────────┐
│ [☰] Logo [⚙]│
├──────────────┤
│              │
│   Content    │
│   Stacked    │
│              │
└──────────────┘
Priority:
1. Session status
2. Critical actions
3. Logs (scrollable)

Tablet (768px-1024px)
┌────────────────────┐
│ Logo Nav [Search]  │
├────────────────────┤
│                    │
│   Content          │
│   Full Width       │
│   (Sidebar overlay)│
│                    │
└────────────────────┘
Priority:
1. Monitoring
2. Quick actions
3. Limited config

Desktop (1024px-1440px)
┌───────────────────────────┐
│ Logo Nav Nav Nav [Search] │
├────────┬──────────────────┤
│ Side   │                  │
│ bar    │   Content Area   │
│        │                  │
└────────┴──────────────────┘
Priority:
All features accessible
Optimal experience

Large Desktop (>1440px)
┌──────────────────────────────────┐
│ Logo Nav Nav Nav Nav [Search]    │
├──────┬───────────────────┬───────┤
│ Side │   Main Content    │ Meta  │
│ bar  │                   │ data  │
│      │                   │       │
└──────┴───────────────────┴───────┘
Priority:
Maximum information density
Three-column layouts
```

---

## Success Metrics Dashboard

### Metrics Hierarchy

```
┌─────────────────────────────────────────────────────────────┐
│ SUCCESS METRICS DASHBOARD                                   │
└─────────────────────────────────────────────────────────────┘

Development Metrics
├── Test Coverage: [████████████████████░] 85%  Target: >80%
├── Accessibility: [████████████████████░] 100% Target: 100%
├── Performance:   [████████████████████░] 92   Target: >90
└── Bundle Size:   [████████████████░░░░░] 180KB Target: <200KB

User Experience Metrics
├── Task Completion:  [████████████████░░] 87%  Target: >85%
├── Time to Session:  [████████████████░░] 8min Target: <10min
├── Status Check:     [████████████████████░] 2s Target: <3s
└── SUS Score:        [████████████████░░] 82   Target: >80

Business Metrics
├── Adoption Rate:    [████████████░░░░░░░] Trending ↑
├── Time Saved:       [████████████████████░] 1,240 hours
├── ROI:              [████████████████░░] +145% Target: Positive
└── Support Tickets:  [████████████████████░] Trending ↓

Legend:
━━━━━━
[████████████████████░] Progress bar (80-100% = Green)
↑ ↓                     Trend indicators
```

---

## Conclusion

These visual diagrams complement the detailed written specifications in the other documents. Use them for:

- **Quick reference** during implementation
- **Team communication** and alignment
- **Stakeholder presentations**
- **Onboarding** new team members

For detailed specifications, refer to:
- UX_ARCHITECTURE_STRATEGY.md
- USER_JOURNEY_MAPS.md
- INFORMATION_ARCHITECTURE.md
- IMPLEMENTATION_ROADMAP.md

---

**Questions?** Contact UX Architecture Team
