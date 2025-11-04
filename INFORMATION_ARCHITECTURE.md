# Information Architecture: Ambient Code Platform
**Document Type**: Detailed IA Specification
**Version**: 1.0
**Date**: 2025-11-04
**Author**: Aria, UX Architect

---

## Table of Contents
1. [IA Principles](#ia-principles)
2. [Site Map](#site-map)
3. [Navigation Systems](#navigation-systems)
4. [Content Organization](#content-organization)
5. [Search & Filtering](#search--filtering)
6. [Labeling System](#labeling-system)
7. [URL Structure](#url-structure)
8. [Responsive IA](#responsive-ia)

---

## 1. IA Principles

### 1.1 Foundational Principles

**Principle 1: Session-Centric Architecture**
- The session is the primary unit of work
- All other content (projects, agents, configurations) supports session creation and management
- Navigation should always make it easy to return to active sessions

**Principle 2: Progressive Disclosure**
- Start with high-level overview, allow drilling into details
- Default views optimized for quick status assessment
- Detailed views available on-demand without context loss

**Principle 3: Persistent Context**
- Users always know where they are in the hierarchy
- Related content is accessible without losing current context
- Breadcrumbs and contextual navigation maintain orientation

**Principle 4: Task-Based Organization**
- Structure follows user tasks, not system architecture
- Primary paths align with common workflows
- Secondary functions accessible but not prominent

**Principle 5: Scalable Structure**
- IA supports growth from single user to enterprise teams
- Hierarchy can accommodate increasing complexity
- Search and filtering become more important at scale

### 1.2 User Mental Models

Users come to the platform with existing mental models from:

**Similar Platforms**:
- Kubernetes Dashboard → Resource management, real-time monitoring
- GitHub Actions → Workflow automation, logs, artifacts
- Jupyter Notebooks → Interactive execution, iterative development
- CI/CD Tools → Pipeline execution, status tracking

**Our IA Should Leverage**:
- Familiar navigation patterns (left sidebar, top nav)
- Recognizable iconography (play/pause/stop for execution)
- Standard terminology (run, deploy, configure)
- Consistent status indicators (success/failure/running)

---

## 2. Site Map

### 2.1 Primary Structure

```
Ambient Code Platform (Root)
│
├── Dashboard (Home)
│   ├── Overview (default)
│   ├── Recent Activity
│   └── Quick Actions
│
├── Projects
│   ├── All Projects (list view)
│   ├── Project Detail
│   │   ├── Overview
│   │   ├── Sessions (related to this project)
│   │   ├── Configuration
│   │   ├── Team Access
│   │   └── History
│   ├── Templates
│   │   ├── Browse Templates
│   │   ├── Template Detail
│   │   ├── My Templates
│   │   └── Create Template
│   └── Create New Project
│
├── Sessions
│   ├── Active Sessions (list view)
│   ├── Session History
│   ├── Session Detail
│   │   ├── Overview (default)
│   │   ├── Agents
│   │   │   ├── Agent List
│   │   │   └── Agent Detail
│   │   │       ├── Activity
│   │   │       ├── Reasoning
│   │   │       ├── Logs
│   │   │       └── Configuration
│   │   ├── Logs (unified view)
│   │   ├── Artifacts
│   │   │   ├── Files Created/Modified
│   │   │   ├── Reports Generated
│   │   │   └── Resources Created
│   │   ├── Metrics
│   │   │   ├── Performance
│   │   │   ├── Resource Usage
│   │   │   └── Cost Tracking
│   │   └── Actions
│   │       ├── Pause/Resume
│   │       ├── Modify Configuration
│   │       ├── Clone & Modify
│   │       └── Export/Share
│   └── Create New Session
│
├── Analytics (PM-focused)
│   ├── Business Metrics
│   │   ├── Time Saved
│   │   ├── Cost Savings
│   │   └── ROI Calculator
│   ├── Adoption & Usage
│   │   ├── User Activity
│   │   ├── Session Trends
│   │   └── Feature Usage
│   ├── Performance
│   │   ├── Success Rates
│   │   ├── Execution Times
│   │   └── Error Rates
│   └── Reports
│       ├── Pre-built Reports
│       ├── Custom Report Builder
│       └── Scheduled Reports
│
├── Settings
│   ├── Profile
│   │   ├── Personal Information
│   │   ├── Preferences
│   │   └── Notifications
│   ├── Integrations
│   │   ├── Connected Accounts
│   │   │   ├── GitHub/GitLab
│   │   │   ├── Container Registries
│   │   │   ├── Kubernetes Clusters
│   │   │   └── Cloud Providers
│   │   ├── API & Webhooks
│   │   │   ├── API Keys
│   │   │   ├── Webhook Configuration
│   │   │   └── API Documentation
│   │   └── Observability
│   │       ├── Metrics Export
│   │       ├── Log Forwarding
│   │       └── External Dashboards
│   ├── AI Models
│   │   ├── Model Providers
│   │   ├── Model Selection
│   │   ├── API Keys
│   │   └── Usage & Costs
│   ├── Resources
│   │   ├── Compute Quotas
│   │   ├── Storage Limits
│   │   └── Network Configuration
│   ├── Team (if applicable)
│   │   ├── Members
│   │   ├── Roles & Permissions
│   │   ├── Team Settings
│   │   └── Billing (if applicable)
│   └── Platform
│       ├── General Settings
│       ├── Security
│       ├── Compliance
│       └── Advanced Configuration
│
└── Help & Documentation
    ├── Getting Started
    ├── Documentation
    ├── API Reference
    ├── Community Forum
    ├── Support
    │   ├── Contact Support
    │   ├── My Tickets
    │   └── Known Issues
    └── About
        ├── Release Notes
        ├── Status Page
        └── Legal
```

### 2.2 Navigation Depth Analysis

```
Level 1 (Global Nav)   Level 2 (Section Nav)   Level 3 (Content)      Level 4+ (Detail)
─────────────────────  ─────────────────────   ──────────────────     ────────────────
Dashboard              Overview                Recent Sessions        Session Detail
                       Recent Activity         Activity Feed          Agent Detail
                       Quick Actions           Shortcuts

Projects               All Projects            Project List           Project Detail
                       Templates               Template Gallery       Template Detail
                       Create New              Creation Wizard

Sessions               Active                  Session List           Session Detail
                       History                 Historical Sessions    Agent Detail
                       Create New              Session Wizard         Log Detail

Analytics              Business Metrics        Metrics Dashboard      Drill-down views
                       Adoption                Usage Charts           User detail
                       Performance             Performance Graphs     Session analysis
                       Reports                 Report List            Report builder

Settings               Profile                 User Settings          Edit forms
                       Integrations            Integration List       Config detail
                       AI Models               Model List             Provider setup
                       Resources               Resource Dashboard     Quota management
                       Team                    Member List            Permission editor
                       Platform                Platform Settings      Advanced config
```

**Depth Guidelines**:
- **Optimal**: 3 levels (Global → Section → Content)
- **Maximum**: 4 levels before requiring modal/overlay
- **Critical content**: Accessible within 2 clicks from dashboard

---

## 3. Navigation Systems

### 3.1 Global Navigation (Top Bar)

**Always Visible Elements**:

```
┌────────────────────────────────────────────────────────────────┐
│ [Logo]  Dashboard  Projects  Sessions  Analytics  [Search]     │
│                                                                 │
│                                              [Alerts] [Profile] │
└────────────────────────────────────────────────────────────────┘
```

**Specifications**:
- **Logo**: Left-aligned, links to Dashboard
- **Primary Nav Items**: Dashboard, Projects, Sessions, Analytics
- **Utility Nav**: Search, Alerts, User Profile (right-aligned)
- **Active Indicator**: Bottom border or background highlight
- **Responsive**: Collapses to hamburger menu on <1024px

**Navigation Item Behaviors**:
- **Click**: Navigates to default view of that section
- **Hover**: Shows dropdown with quick links (optional)
- **Keyboard**: Arrow keys navigate, Enter selects

### 3.2 Contextual Navigation (Left Sidebar)

**Dynamic Based on Context**:

When on **Dashboard**:
```
┌─────────────────────┐
│ Overview            │
│ Recent Activity     │
│ Quick Actions       │
│ Bookmarks           │
└─────────────────────┘
```

When on **Sessions > Session Detail**:
```
┌─────────────────────┐
│ Overview            │
│ Agents              │
│   • Planning Agent  │
│   • Code Agent      │
│   • Test Agent      │
│ Logs                │
│ Artifacts           │
│ Metrics             │
│ Actions             │
│ ─────────────────── │
│ ← Back to Sessions  │
└─────────────────────┘
```

When on **Settings**:
```
┌─────────────────────┐
│ Profile             │
│ Integrations        │
│ AI Models           │
│ Resources           │
│ Team                │
│ Platform            │
└─────────────────────┘
```

**Specifications**:
- **Width**: 240px default, collapsible to 60px (icons only)
- **Hierarchy**: Up to 2 levels of indentation
- **Active State**: Background highlight + left border accent
- **Collapse Control**: Icon at bottom of sidebar
- **Persistent**: Maintains state across page navigation

### 3.3 Breadcrumbs

**Always Present Below Top Navigation**:

```
┌────────────────────────────────────────────────────────────────┐
│ Home > Projects > My API Project > Session #42 > Code Agent    │
└────────────────────────────────────────────────────────────────┘
```

**Specifications**:
- **Separator**: ">" or "/"
- **Clickable**: All ancestors are clickable links
- **Current Page**: Not clickable, slightly dimmed or different style
- **Truncation**: Middle truncation on long names (e.g., "My Very Lo...ject")
- **Mobile**: Show last 2 levels only

**Dynamic Breadcrumb Examples**:
```
Sessions > Active > Web App Deploy > Planning Agent
Projects > My API Project > Configuration
Settings > Integrations > GitHub > Repository Access
Analytics > Reports > Monthly ROI Report
```

### 3.4 In-Page Navigation (Tabs)

**Used for Related Content Views**:

```
┌────────────────────────────────────────────────────────────────┐
│ [Overview]  [Agents]  [Logs]  [Artifacts]  [Metrics]  [Actions]│
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│                     Content Area                                │
│                                                                 │
└────────────────────────────────────────────────────────────────┘
```

**Specifications**:
- **Style**: Underline or background for active tab
- **Overflow**: Horizontal scroll or "More" dropdown on narrow screens
- **Keyboard**: Arrow keys to navigate between tabs
- **Deep Linking**: Tab selection persists in URL

**Use Cases**:
- Session Detail views (Overview, Agents, Logs, etc.)
- Project Detail views (Overview, Sessions, Configuration, etc.)
- Settings sections (Profile, Integrations, etc.)

### 3.5 Contextual Actions (Page Header)

**Action Buttons in Header**:

```
┌────────────────────────────────────────────────────────────────┐
│ Session #42: Web App Deploy                    [Clone] [Stop]  │
│ Status: Running • Started 15 minutes ago       [Export] [More] │
├────────────────────────────────────────────────────────────────┤
```

**Specifications**:
- **Primary Action**: Solid button (e.g., "Create", "Start")
- **Secondary Actions**: Outlined buttons
- **Destructive Actions**: Red outlined button
- **Overflow**: "More" dropdown for additional actions
- **Responsive**: Collapse to icon buttons on mobile

---

## 4. Content Organization

### 4.1 Dashboard Organization

**Card-Based Layout**:

```
┌─────────────────┬─────────────────┬─────────────────┐
│ Active Sessions │ Recent Projects │ Quick Create    │
│                 │                 │                 │
│ • Session A     │ • Project 1     │ [Templates]     │
│ • Session B     │ • Project 2     │ [From Scratch]  │
│ • Session C     │ • Project 3     │                 │
│ [View All]      │ [View All]      │                 │
└─────────────────┴─────────────────┴─────────────────┘
┌─────────────────────────────────────────────────────┐
│ Activity Feed                                       │
│                                                     │
│ • Session "API Update" completed successfully       │
│ • New template "FastAPI Starter" shared by Jordan  │
│ • Warning: High resource usage in Session #38      │
│ [View All Activity]                                 │
└─────────────────────────────────────────────────────┘
┌─────────────────┬─────────────────┬─────────────────┐
│ Time Saved      │ Success Rate    │ Active Users    │
│ This Month      │ Last 30 Days    │ Right Now       │
│                 │                 │                 │
│  24.5 hours     │     94%         │      12         │
└─────────────────┴─────────────────┴─────────────────┘
```

**Customization**:
- Users can rearrange cards (drag and drop)
- Show/hide cards based on persona or preference
- Default layouts per persona type

### 4.2 List Views

**Standard Table Pattern** (e.g., Sessions List):

```
┌────────────────────────────────────────────────────────────────┐
│ [Filters ▼] [Search...]                    [Create Session +]  │
├────────────────────────────────────────────────────────────────┤
│ □ Name              Status    Project      Started      Actions│
├────────────────────────────────────────────────────────────────┤
│ □ API Endpoint Add  ● Running MyAPI        2m ago       [Stop] │
│ □ Test Suite Run    ✓ Complete WebApp      1h ago       [View] │
│ □ Refactor Auth     ⊗ Failed  AuthService  3h ago       [Retry]│
│ □ Deploy Staging    ○ Queued  MainApp      5m ago       [Edit] │
├────────────────────────────────────────────────────────────────┤
│                    [← Prev]  Page 1 of 4  [Next →]             │
└────────────────────────────────────────────────────────────────┘
```

**Features**:
- **Bulk Selection**: Checkboxes for bulk actions
- **Sortable Columns**: Click headers to sort
- **Filterable**: Dropdown filters + search
- **Row Actions**: Hover reveals action buttons
- **Expandable Rows**: Click row to expand inline details (optional)
- **Pagination**: Standard pagination or infinite scroll

**Column Priorities** (for responsive):
1. Name (always visible)
2. Status (always visible)
3. Project (hide on tablet)
4. Started (hide on mobile)
5. Actions (always visible, may collapse to menu)

### 4.3 Detail Views

**Consistent Pattern Across All Detail Pages**:

```
┌────────────────────────────────────────────────────────────────┐
│ [Breadcrumbs]                                                  │
├────────────────────────────────────────────────────────────────┤
│ [Icon] Title/Name                        [Primary] [Secondary] │
│        Status/Meta Information           [Actions] [More ▼]    │
├────────────────────────────────────────────────────────────────┤
│ [Tab 1] [Tab 2] [Tab 3] [Tab 4]                               │
├────────────────────────────────────────────────────────────────┤
│                                                                 │
│                     Main Content Area                           │
│                                                                 │
│  Two-column layout where appropriate:                          │
│  ┌──────────────────────┬───────────────┐                     │
│  │ Primary Content      │ Sidebar       │                     │
│  │ (70%)                │ (30%)         │                     │
│  │                      │               │                     │
│  │                      │ • Metadata    │                     │
│  │                      │ • Quick Stats │                     │
│  │                      │ • Related     │                     │
│  └──────────────────────┴───────────────┘                     │
│                                                                 │
└────────────────────────────────────────────────────────────────┘
```

**Consistency Rules**:
- Page header always contains: breadcrumbs, title, status, actions
- Tabs for distinct content categories
- Sidebar (when present) for metadata, stats, related items
- Actions grouped by frequency: primary (most common), secondary, more menu

### 4.4 Empty States

**Encourage Action with Helpful Empty States**:

```
┌────────────────────────────────────────────────────────────────┐
│                                                                 │
│                        [Illustration]                           │
│                                                                 │
│                  No Sessions Yet                                │
│                                                                 │
│    Sessions are automated workflows that execute tasks          │
│    using AI agents. Get started by creating your first one.    │
│                                                                 │
│              [Create from Template]  [Start Fresh]              │
│                                                                 │
│                      [Watch Tutorial]                           │
│                                                                 │
└────────────────────────────────────────────────────────────────┘
```

**Empty State Requirements**:
- **Visual**: Illustration or icon (not just text)
- **Explanation**: What this section is for
- **Action**: Clear call-to-action button
- **Help**: Link to documentation or tutorial

**Context-Specific Examples**:
- **No Active Sessions**: "Create your first session"
- **No Search Results**: "Try different keywords or filters"
- **No Integrations**: "Connect your first service"
- **No Team Members**: "Invite team members"

---

## 5. Search & Filtering

### 5.1 Global Search

**Location**: Top navigation bar, right side

```
┌────────────────────────────────────────────────────────────────┐
│ [🔍 Search sessions, projects, docs...]                        │
├────────────────────────────────────────────────────────────────┤
│ Recent Searches                                                │
│ • "API authentication"                                         │
│ • "failed sessions"                                            │
│                                                                 │
│ Suggestions                                                    │
│ Sessions                                                       │
│ • Session #42: API Endpoint Addition                          │
│ • Session #38: Auth Refactor                                  │
│                                                                 │
│ Projects                                                       │
│ • My API Project                                              │
│                                                                 │
│ Documentation                                                  │
│ • Configuring Agents                                          │
│ • Troubleshooting Failed Sessions                             │
│                                                                 │
│ [View All Results →]                                           │
└────────────────────────────────────────────────────────────────┘
```

**Search Capabilities**:
- **Indexed Content**: Sessions, projects, templates, documentation, settings
- **Search Operators**: Support for quotes, AND/OR, field-specific (name:api)
- **Filters**: Type, status, date range
- **Keyboard Shortcut**: Cmd/Ctrl + K to open
- **Live Results**: As-you-type suggestions

**Search Results Page**:
```
┌────────────────────────────────────────────────────────────────┐
│ [🔍 "API authentication"] [All Results ▼] [Filters]           │
├────────────────────────────────────────────────────────────────┤
│ Found 23 results                                               │
│                                                                 │
│ Sessions (12)                                                  │
│ ├─ API Endpoint Addition                                      │
│ │  Running • Started 2h ago • MyAPI Project                   │
│ │  ...implementing JWT authentication for API...              │
│ │                                                              │
│ └─ Auth Refactor                                              │
│    Failed • 3h ago • AuthService Project                      │
│    ...adding OAuth2 authentication...                         │
│                                                                 │
│ Projects (3)                                                   │
│ ├─ My API Project                                             │
│ │  12 sessions • Last active 2h ago                           │
│ │                                                              │
│ Documentation (8)                                              │
│ ├─ Configuring Authentication Agents                          │
│ │  Learn how to configure agents for auth tasks...            │
│                                                                 │
│ [Load More]                                                    │
└────────────────────────────────────────────────────────────────┘
```

### 5.2 Contextual Filtering

**Filter Pattern for List Views**:

```
┌────────────────────────────────────────────────────────────────┐
│ [Status ▼] [Project ▼] [Date Range ▼] [More Filters +]        │
├────────────────────────────────────────────────────────────────┤
│ Active Filters:                                                │
│ • Status: Running [×]                                          │
│ • Project: MyAPI [×]                                           │
│ [Clear All]                                                    │
└────────────────────────────────────────────────────────────────┘
```

**Filter Interactions**:
- **Multi-select**: Can select multiple values per filter
- **Clear Individual**: X button to remove single filter
- **Clear All**: Reset all filters at once
- **Filter Counts**: Show result count before applying
- **Persistent**: Filters persist in URL for sharing

**Standard Filters by Context**:

**Sessions**:
- Status (Running, Completed, Failed, Paused)
- Project
- Date Range
- Agent Type
- Duration

**Projects**:
- Status (Active, Archived)
- Template Used
- Owner/Team Member
- Created Date

**Agents** (within session):
- Status
- Type (Planning, Code, Test, etc.)
- Duration
- Success/Failure

### 5.3 Advanced Search

**Accessible via "Advanced Search" link**:

```
┌────────────────────────────────────────────────────────────────┐
│ Advanced Search                                     [Search]   │
├────────────────────────────────────────────────────────────────┤
│ Keywords:        [                                    ]        │
│ Type:            [All ▼] Sessions  Projects  Templates         │
│ Status:          [All ▼] Running  Completed  Failed            │
│ Date Range:      [Last 7 days ▼] From: [    ] To: [    ]     │
│ Project:         [All Projects ▼]                              │
│ Created By:      [Anyone ▼]                                    │
│ Duration:        Min: [    ] Max: [    ] minutes               │
│                                                                 │
│ [Reset]                                         [Search]       │
└────────────────────────────────────────────────────────────────┘
```

---

## 6. Labeling System

### 6.1 Terminology Standards

**Consistent Terms Across Platform**:

| Concept | Standard Label | Avoid | Rationale |
|---------|---------------|-------|-----------|
| Unit of work | Session | Job, Run, Execution | Familiar from Jupyter, clear |
| AI entity | Agent | Bot, Assistant, Worker | Industry standard, anthropomorphic |
| Collection | Project | Workspace, Repository | Familiar from IDEs |
| Output | Artifact | File, Output, Result | More precise |
| Decision process | Reasoning | Thinking, Chain of Thought | Non-technical |
| User action | Intervention | Override, Stop, Interrupt | Empowering |
| Agent activity | Action | Step, Task, Operation | Clear and active |
| View details | View | See, Show, Display | Consistent action verb |
| Make changes | Configure | Settings, Options, Preferences | Active verb |

### 6.2 Status Labels

**Session Status**:
```
● Running     (blue, animated)
○ Queued      (gray)
▸ Starting    (blue, animated)
‖ Paused      (orange)
✓ Completed   (green)
⊗ Failed      (red)
⚠ Warning     (yellow)
↻ Retrying    (blue, animated)
```

**Agent Status**:
```
● Active      (blue)
○ Waiting     (gray)
✓ Complete    (green)
⊗ Failed      (red)
⚠ Warning     (yellow)
⏸ Paused     (orange)
```

### 6.3 Action Labels

**Button Labels** (Verb + Noun when needed):

**Primary Actions**:
- Create Session
- Start Session
- Create Project
- Save Changes
- Apply Configuration

**Secondary Actions**:
- Clone Session
- Export Logs
- View Details
- Configure Agent
- Edit Settings

**Destructive Actions**:
- Stop Session
- Delete Project
- Remove Member
- Disconnect Integration

**Principle**: Use action verbs, be specific about what will happen

---

## 7. URL Structure

### 7.1 URL Patterns

**Structure**: `/{collection}/{id}/{view}?{params}`

**Examples**:

```
/dashboard
/dashboard?view=activity

/projects
/projects/new
/projects/{project-id}
/projects/{project-id}/sessions
/projects/{project-id}/configuration
/projects/{project-id}/team

/templates
/templates/{template-id}
/templates/{template-id}/preview

/sessions
/sessions?status=running&project=myapi
/sessions/new
/sessions/new?template={template-id}
/sessions/{session-id}
/sessions/{session-id}/agents
/sessions/{session-id}/agents/{agent-id}
/sessions/{session-id}/logs
/sessions/{session-id}/artifacts
/sessions/{session-id}/metrics

/analytics
/analytics/business-metrics
/analytics/adoption
/analytics/performance
/analytics/reports
/analytics/reports/{report-id}

/settings
/settings/profile
/settings/integrations
/settings/integrations/{integration-type}
/settings/ai-models
/settings/resources
/settings/team
/settings/platform

/help
/help/getting-started
/help/docs
/help/docs/{doc-id}
/help/support
/help/support/tickets/{ticket-id}
```

### 7.2 URL Design Principles

1. **Readable**: Use human-readable slugs, not UUIDs in URLs
   - Good: `/sessions/api-endpoint-addition-42`
   - Bad: `/sessions/a3f2c9d8-4b7a-4e9c-8d3f-2c9d8a3f2c9d`

2. **Hierarchical**: Reflect content hierarchy
   - `/projects/{project-id}/sessions` shows sessions belong to project

3. **Consistent**: Same patterns across different content types

4. **Parameters for Filters**: Use query params for view variations
   - `/sessions?status=running&project=myapi`

5. **Deep Linkable**: Every view should have a unique URL

6. **Shareable**: URLs should work when shared with team members

---

## 8. Responsive IA

### 8.1 Breakpoint Strategy

```
Mobile:      < 768px
Tablet:      768px - 1024px
Desktop:     1024px - 1440px
Large:       > 1440px
```

### 8.2 Navigation Adaptation

**Desktop (>1024px)**:
```
┌─────────────────────────────────────────────────────────┐
│ [Logo] Dashboard Projects Sessions Analytics  [Search]  │
│                                              [Alerts][⚙]│
├────────────┬────────────────────────────────────────────┤
│ Sidebar    │                                            │
│ - Overview │           Main Content                     │
│ - Agents   │                                            │
│ - Logs     │                                            │
│ - Metrics  │                                            │
└────────────┴────────────────────────────────────────────┘
```

**Tablet (768px - 1024px)**:
```
┌─────────────────────────────────────────────────────────┐
│ [Logo] Dashboard Projects Sessions  [☰] [Search] [⚙]   │
├─────────────────────────────────────────────────────────┤
│                                                          │
│           Main Content (Full Width)                      │
│           Sidebar collapsed or overlay                   │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

**Mobile (<768px)**:
```
┌──────────────────────────────────┐
│ [☰] Ambient [Search] [⚙]        │
├──────────────────────────────────┤
│                                  │
│                                  │
│        Main Content              │
│        (Stacked)                 │
│                                  │
│                                  │
└──────────────────────────────────┘
```

### 8.3 Content Prioritization

**What to Show on Mobile**:

Priority 1 (Always visible):
- Session status
- Critical actions (Stop, Pause)
- Current state
- Error messages

Priority 2 (Accessible via tap/expand):
- Agent details
- Logs (scrollable)
- Configuration

Priority 3 (Link to full view):
- Detailed metrics
- Historical data
- Complex configurations

**Mobile-Specific Patterns**:
- **Bottom Sheet**: For actions and details
- **Swipe Actions**: For common row actions in lists
- **Collapsible Sections**: All sections collapsed by default
- **Sticky Headers**: Keep context while scrolling

---

## 9. Accessibility Considerations in IA

### 9.1 Keyboard Navigation

**Tab Order**:
1. Skip to main content link
2. Logo/Home link
3. Primary navigation (left to right)
4. Search
5. Utility navigation (Alerts, Profile)
6. Main content area
7. Secondary navigation (sidebar/tabs)
8. Footer links

**Keyboard Shortcuts**:
```
Global:
Cmd/Ctrl + K     Open search
Cmd/Ctrl + /     Show keyboard shortcuts
Escape           Close modal/overlay

Navigation:
G then D         Go to Dashboard
G then P         Go to Projects
G then S         Go to Sessions
G then A         Go to Analytics

Actions:
C                Create new (context-dependent)
E                Edit (when viewing detail)
R                Refresh
```

### 9.2 Screen Reader Structure

**Landmark Regions**:
```html
<banner>     Top navigation
<navigation> Primary navigation, sidebar navigation
<main>       Main content area
<search>     Search functionality
<form>       Configuration forms
<contentinfo> Footer
```

**Heading Hierarchy**:
```
h1 - Page title (one per page)
h2 - Major sections
h3 - Subsections
h4 - Component titles
h5, h6 - Rarely needed
```

**ARIA Labels for Dynamic Content**:
```html
aria-live="polite"    For status updates
aria-live="assertive" For critical errors
role="status"         For loading states
role="alert"          For error messages
aria-busy="true"      During loading
```

---

## 10. IA Evolution & Governance

### 10.1 Scalability Considerations

**Current State** (MVP):
- Single-user focused
- Limited project organization
- Basic analytics

**Future States**:

**Phase 2** (Team Features):
- Add: Team workspace level above projects
- Add: Shared templates library
- Add: Team activity feed
- Navigation impact: Additional hierarchy level

**Phase 3** (Enterprise):
- Add: Organization level above teams
- Add: Compliance/audit section
- Add: Advanced permissions management
- Navigation impact: Role-based navigation variants

**Phase 4** (Marketplace):
- Add: Template marketplace
- Add: Agent marketplace
- Add: Integration marketplace
- Navigation impact: Browse/discover sections

### 10.2 IA Maintenance

**Regular Reviews**:
- **Monthly**: Analytics review of navigation usage
- **Quarterly**: User testing of key workflows
- **Bi-annually**: Complete IA audit

**Key Metrics to Monitor**:
- Navigation patterns (where do users go?)
- Search queries (what are they looking for?)
- Drop-off points (where do they get lost?)
- Support tickets (IA-related confusion?)

**Change Process**:
1. Identify IA issue (data-driven)
2. Propose solution
3. Prototype and test
4. Implement with announcement
5. Monitor impact

---

## Appendix A: IA Decision Log

| Date | Decision | Rationale | Impact |
|------|----------|-----------|--------|
| 2025-11-04 | Session-centric architecture | Users primarily interact with sessions | Major: Core IA structure |
| 2025-11-04 | Analytics as top-level section | PM persona needs prominent access | Medium: Navigation addition |
| 2025-11-04 | Settings consolidated | Reduce navigation clutter | Medium: Clearer structure |
| 2025-11-04 | Help moved to footer/profile | Not primary task | Minor: Reduced top nav |

---

## Appendix B: Navigation Usability Heuristics

**Checklist for All Navigation Decisions**:

- [ ] Can users determine their current location?
- [ ] Can users access any section within 3 clicks?
- [ ] Are navigation labels clear and jargon-free?
- [ ] Is navigation consistent across the platform?
- [ ] Can users return to previous locations easily?
- [ ] Are critical actions always accessible?
- [ ] Does navigation scale with content growth?
- [ ] Is navigation fully keyboard accessible?
- [ ] Do screen readers announce navigation clearly?
- [ ] Are mobile and desktop navigation patterns intuitive?

---

**Document Maintenance**: Update when significant IA changes are implemented.

**Questions?** Contact UX Architecture Team
