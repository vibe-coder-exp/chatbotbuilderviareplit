# AI Chatbot Agency Admin Dashboard - Design Guidelines

## Design Approach
**Reference-Based System Approach**: This is a utility-focused admin dashboard requiring efficiency and clarity. Drawing inspiration from modern SaaS dashboards like Linear, Vercel, and Stripe admin panels, with emphasis on clean data presentation and intuitive workflows.

## Core Design Principles
- **Clean & Minimal**: White/light-gray backgrounds with generous whitespace
- **Soft & Modern**: Rounded corners (2xl), subtle shadows, gentle gradients
- **Data-Focused**: Clear hierarchy for tables, statistics, and form inputs
- **Professional SaaS Aesthetic**: Polished, trustworthy interface for business operations

---

## Typography
**Font Family**: Inter or Poppins from Google Fonts CDN
- **Headings**: Font weight 600-700, sizes ranging from text-2xl to text-4xl
- **Body Text**: Font weight 400-500, text-sm to text-base
- **Labels**: Font weight 500-600, text-xs to text-sm uppercase tracking-wide
- **Data/Stats**: Font weight 700, text-3xl to text-5xl for emphasis

---

## Layout System
**Spacing Units**: Use Tailwind units of 2, 4, 6, 8, 12, 16, 20, 24 for consistent rhythm
- **Card Padding**: p-6 to p-8 for desktop, p-4 to p-6 for mobile
- **Section Spacing**: mb-6 to mb-8 between major sections
- **Form Fields**: gap-4 to gap-6 between inputs
- **Page Margins**: Container max-width with px-4 to px-8

**Grid Systems**:
- Statistics Cards: 3-column grid on desktop (grid-cols-1 md:grid-cols-2 lg:grid-cols-3)
- Settings Layout: 2-column layout (form + preview) on desktop, stack on mobile
- Bot Table: Full-width responsive table with horizontal scroll on mobile

---

## Color Strategy
**Primary Theme**: Blue-purple gradient system
- Login background: Linear gradient from blue (#4f46e5) to purple (#7c3aed)
- Accent colors: Use primary theme color selected per bot
- Neutral palette: Gray-50 to gray-900 for backgrounds, borders, text
- Status indicators: Green for active, yellow for pending, red for inactive

**Application**:
- Page backgrounds: Gray-50 or white
- Card backgrounds: White with subtle shadow
- Sidebar: White or very light gray (gray-50)
- Hover states: Lighter shade of primary or gray-100

---

## Component Library

### Navigation Components
**Sidebar** (Fixed Left):
- Width: 64 (collapsed icons) or 256 (expanded)
- Background: White with subtle right border
- Navigation items with icons (Dashboard, Bots, Settings)
- Active state: Primary color background with rounded corners
- Collapsible on mobile with overlay

**Navbar** (Top):
- Height: 16 to 20
- Logo on left, logout/profile on right
- Background: White with bottom border or subtle shadow
- Responsive: Hamburger menu on mobile

### Data Display
**Statistics Cards**:
- Rounded-2xl borders with soft shadow (shadow-sm to shadow-md)
- Icon in colored circle (bg-blue-100, text-blue-600)
- Large numeric value (text-3xl font-bold)
- Small descriptive label below (text-sm text-gray-500)
- Minimal padding p-6

**Data Table**:
- Striped rows (alternate gray-50 background)
- Header: Font-semibold, text-xs uppercase, bg-gray-50, sticky top
- Borders: Subtle gray-200 borders between rows
- Actions column: Icon buttons (edit/delete) with hover effects
- Responsive: Horizontal scroll container on mobile

**Bot List/Grid**:
- Cards with bot name, client, status badge
- Edit/delete actions on hover or always visible on mobile
- Grid layout: 1 column mobile, 2-3 columns desktop

### Forms & Inputs
**Form Fields**:
- Labels: Font-medium text-sm mb-2 block
- Inputs: Rounded-lg border-gray-300 focus:border-primary focus:ring-2
- Height: h-10 to h-12 for text inputs
- Textarea: min-h-24 with resize capability
- Color picker: Custom rounded component with swatch preview

**Buttons**:
- Primary: bg-primary text-white rounded-lg px-6 py-2.5 font-medium
- Secondary: bg-white border-gray-300 text-gray-700 rounded-lg
- Danger: bg-red-600 text-white for delete actions
- Icon buttons: Square (w-10 h-10) rounded-lg with centered icon

**Modal/Dialog**:
- Overlay: bg-black/50 backdrop-blur-sm
- Content: bg-white rounded-2xl max-w-2xl p-6 to p-8
- Header: text-xl font-semibold mb-6
- Footer: Flex justify-end with gap-3 for buttons
- Close button: Top-right corner with X icon

### Specialized Components
**Embed Code Display**:
- Monospace font (font-mono)
- Dark background (bg-gray-900 text-gray-100) or light (bg-gray-50)
- Rounded-lg with p-4
- Copy button in top-right corner
- Syntax highlighting optional but nice

**Chat Preview Window**:
- Iframe-style container showing bot appearance
- Rounded corners matching selected bot style
- Max width 400-500px, responsive scaling
- Shadow-lg for elevation

**Theme/Color Picker**:
- Visual swatch grid or color input
- Live preview of selected color
- Preset palette options displayed as circular swatches

---

## Page-Specific Layouts

### Login Page
- Centered card (max-w-md) on gradient background
- Card: bg-white rounded-2xl shadow-2xl p-8
- Logo/title centered at top
- Form fields stacked with mb-4
- Full-width primary button
- Background: Full-viewport blue-purple gradient

### Dashboard Page
- Sidebar + main content area layout
- Top row: 3 statistics cards in grid
- Below: Recent activity section with list items
- Each activity item: Icon, text, timestamp in flex layout
- "Create New Bot" button: Top-right of main area, primary style

### Bots Page
- Header with page title and "Create New Bot" button (justify-between)
- Data table below showing all bots
- Table columns: Bot Name (font-medium) | Client | Status (badge) | Created (text-gray-500) | Actions (icons)
- Modal for create/edit with comprehensive form fields in 2-column grid where appropriate

### Settings Page
- Two-column layout on desktop
- Left: Form sections (Admin Info, Default Theme) with cards
- Right: Live preview of bot with current settings
- Each section in white rounded-2xl card with p-6
- Save button at bottom or sticky top-right

### Embed Preview Page
- Centered layout with max-w-4xl
- Code snippet box at top with copy button
- Visual preview below in bordered container
- Instructions or help text in muted color

---

## Responsive Behavior
**Breakpoints**:
- Mobile: Base (< 768px) - single column, stacked layout, collapsed sidebar
- Tablet: md (768px+) - 2-column grids, sidebar visible or toggleable
- Desktop: lg (1024px+) - full layout with expanded sidebar, 3-column grids

**Mobile Optimizations**:
- Sidebar becomes overlay drawer with close button
- Statistics cards stack vertically
- Tables scroll horizontally in container
- Form fields full-width
- Modals take more viewport space (max-w-full with margins)

---

## Icons
**Library**: Lucide-react via CDN
- Navigation: Menu, LayoutDashboard, Bot, Settings, LogOut
- Statistics: Activity, MessageSquare, Clock
- Actions: Edit, Trash2, Copy, Check, X
- Forms: ChevronDown, Upload, Link
- Size: w-5 h-5 for navigation, w-4 h-4 for inline, w-6 h-6 for feature icons

---

## Interactive States
- **Hover**: Subtle background change (gray-50) or scale-105 for cards
- **Active/Selected**: Primary color background with white text
- **Focus**: Ring-2 ring-primary ring-offset-2 for inputs
- **Disabled**: opacity-50 cursor-not-allowed

---

## Images
This dashboard is primarily data and form-focused with minimal imagery needs:
- **Logo**: Company/agency logo in navbar (h-8 to h-10)
- **Bot Preview**: Rendered chat interface in settings preview pane
- **Profile Avatar**: Small circular avatar (w-10 h-10) in navbar, placeholder if no image
- **Empty States**: Optional simple illustrations for "No bots yet" states

No hero images required for this admin interface.