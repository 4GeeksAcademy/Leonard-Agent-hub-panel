# AgentHub Admin Panel — Prototype Specification

## 1. Product description

AgentHub is a SaaS platform for renting specialized AI agents to businesses that need task-specific automation. The product lets companies browse pre-configured agents, attach skills (like web browsing, document analysis, or calendar management), and deploy those agents for operational workflows. The admin panel is built for internal operators who monitor performance, manage users and contracts, review active skills, and investigate errors across the platform.

The admin user is a platform operator or internal staff member responsible for revenue oversight, customer onboarding, operational health, and platform governance. They need a fast, high-visibility dashboard with key metrics and the ability to drill into user records, agent configuration, contracts, and error events without leaving the admin interface.

## 2. Tech stack and constraints

- The prototype must be implemented as static HTML files served from the repository root.
- Styling must use Tailwind CSS via CDN and utility classes only; no external CSS file and no inline style attributes.
- Interactions must be implemented with vanilla JavaScript only; no React, Vue, jQuery, or build tooling.
- The prototype must contain hardcoded data only; no API calls, no backend connectivity, and no persistence beyond the browser session.
- The layout must be responsive for desktop and tablet widths, with the sidebar remaining visible on larger screens and reflowing gracefully on smaller widths.
- The interface must support both light and dark modes using Tailwind's dark mode classes and a single shared UI state.
- All modules should be semantic: use section, nav, header, main, table, aside, and other structural elements appropriately.

## 3. Section specifications

### 3.1 Dashboard

1. A dashboard summary area uses four metric cards in a responsive 2x2 grid on desktop, stacked into two columns at tablet width, each containing an icon, a label, and a hardcoded value such as $48,200, $3,420, 184, and 12.
2. Each metric card uses a distinct accent color and subtle shadow to communicate the metric type: revenue in emerald or blue, discount losses in amber, active agents in violet, and failing agents in red.
3. A full-width placeholder panel appears directly beneath the cards and is styled with a dashed border, neutral background, and centered text label reading “Weekly activity chart” to represent the future analytics view.
4. The dashboard header includes a title, a short subtitle, and a date indicator so the admin can quickly orient to the current reporting period.
5. Cards include a compact trend or delta badge to make the UI feel more realistic without requiring real data connections.

### 3.2 User Management

1. The user management section contains a table with at least five hardcoded user rows showing name, email, plan, status, and a vertical ellipsis action button in the final column.
2. Each table row includes a status badge that uses distinct color treatment for active, trial, suspended, and pending states, and the rows sit in a clean bordered table with subtle hover states.
3. Clicking the ellipsis opens a small dropdown menu with two actions: “View detail” and “Delete.” The dropdown is positioned relative to the button, closes when clicked outside, and uses consistent spacing and hover feedback.
4. Selecting “View detail” opens a modal overlay that shows the full user record, including the user profile details and account metadata, and closes by either clicking the close button or the modal backdrop.
5. The table and modal follow a professional admin style with muted borders, clear hierarchy, and alignment matching the rest of the panel.

### 3.3 Agent Management

1. The agent management view lists at least four agents in a card-based layout, each showing the agent name, owner, status tag, and a compact expand/collapse control for the skill list.
2. Each agent card contains a hidden skill list collapsed by default, and when the expand control is activated the skill items slide open smoothly with a visible transition and a height animation or equivalent motion effect.
3. Every agent card includes a vertical ellipsis action button with menu actions “Configure” and “Delete,” and the menu behavior matches the other action dropdowns across the app.
4. Selecting “Configure” opens a modal overlay containing the full system prompt in an editable textarea for future configuration work; the modal includes a save-type action button and a close control.
5. The status states use consistent colors for active, inactive, and failing states, and the panel should clearly distinguish between operational health and disabled or flagged deployments.

### 3.4 Skills

1. The skills catalog is displayed as a grid of cards, each containing a skill name, a short description, and a compact count such as “Enabled on 12 agents” to show adoption across the fleet.
2. A short explanatory note sits above or below the grid stating that a skill represents a capability or tool that can be attached to an agent and expanded for a given business workflow.
3. Each skill card includes a vertical ellipsis action button with “View detail” and “Delete,” and the dropdown behavior is consistent with all other menu patterns in the app.
4. All skill cards are visually distinct but share a common card frame, label hierarchy, and spacing so they feel like part of a unified admin catalog.
5. The view should remain readable at tablet widths with a responsive grid and clear truncation or wrapping behaviors for longer descriptions.

### 3.5 Agent Contracts

1. The contract table displays at least four hardcoded entries showing client name, rented agent, contracted skills, dates, and total amount paid in a bordered table layout.
2. Each row includes an ellipsis action button with a menu containing “View detail,” following the same interaction model used in other tables and modals.
3. Selecting “View detail” opens a modal containing the full contract breakdown, including a list of itemized skills and individual prices along with the total invoice amount.
4. The contract table uses a readable hierarchy for contract dates and totals, with amounts formatted as currency and skill names grouped in a compact, scannable style.
5. The data should reference the same agent names used elsewhere in the admin panel so the prototype reads as a coherent product rather than isolated sections.

### 3.6 Error Log

1. The error log section contains at least six rows, each with a timestamp, agent name, error type badge, and a phrase summary describing the failure condition.
2. Error rows use distinct badge colors by type or severity (for example, warning, critical, timeout, auth, and runtime), and the log should be visually scannable even when all entries are visible at once.
3. Each row has a vertical ellipsis menu with actions “View detail” and “Mark as resolved,” and both actions maintain the same behavior and styling as the other dropdown-driven interactions.
4. Selecting “View detail” opens a modal showing the full execution trace, including a longer description and a timestamped sequence, while still keeping the layout inside a single professional panel.
5. The log section uses compact but legible text and supports a readable visual rhythm so the admin can spot failure clusters quickly.

## 4. Component inventory

The interface should reuse a standard set of shared UI components across sections:

- Sidebar navigation with section labels and active state indicator
- Metric card with icon, label, value, subtitle, and accent color
- Action dropdown triggered by a vertical ellipsis button
- Modal dialog with close button and backdrop dismissal
- Status badge for plan, agent health, and error severity
- Collapsible skill list inside agent cards with smooth reveal animation
- Dark mode toggle in the top bar using Tailwind dark utilities
- Table and row patterns for users, contracts, and error logs
- Card layouts for agent and skill management sections
- Empty chart placeholder panel for future data visualizations

## 5. Acceptance criteria

1. The repository contains a committed SPECS.md file before any HTML or CSS implementation is added.
2. The specification includes a product description, a technology and constraints section, six section-level requirement groups with at least three concrete specifications each, a component inventory, and a numbered acceptance criteria list.
3. The prototype includes all six primary sections in the sidebar: Dashboard, User Management, Agent Management, Skills, Agent Contracts, and Error Log.
4. Tailwind CSS is loaded through the CDN, and the interface uses utility classes throughout rather than custom CSS or inline style attributes.
5. The dashboard displays four metric cards with labels and values and a chart placeholder beneath them.
6. The user management table includes at least five users and each row contains a working ellipsis dropdown with “View detail” and “Delete.”
7. Selecting “View detail” in the user section opens a modal and the modal closes when the close button is clicked and when the backdrop is clicked.
8. The agent management section includes at least four agents with collapsed skill lists that expand and collapse on click with a visible transition.
9. Each agent row has an ellipsis menu with “Configure” and “Delete,” and “Configure” opens a modal with an editable textarea showing the system prompt.
10. The skills section includes at least four skill cards and a short explanatory description of what a skill is in the AgentHub context.
11. The contracts table shows at least four entries and the “View detail” action opens a modal with itemized skill pricing and the total amount.
12. The error log includes at least six entries with colored severity badges and each row has a dropdown with “View detail” and “Mark as resolved.”
13. The top bar contains a dark/light mode toggle that changes the entire interface and preserves the selected mode while navigating between sections.
14. All dropdown menus close when clicked outside their menu area, and all modals close when clicking the backdrop.
15. The prototype uses consistent hardcoded names across user, agent, contract, and error sections so the data reads as one coherent product.
16. The page uses semantic HTML structure such as header, nav, main, section, aside, and table elements in a clear, accessible layout.

## 6. Implementation note

This specification acts as the implementation contract for the prototype. It is intentionally detailed enough that an AI coding agent or another developer should be able to build the panel without additional clarification. The prototype is a static reference and is not expected to connect to a backend or live data sources.
