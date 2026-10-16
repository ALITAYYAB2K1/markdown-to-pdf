# UI/UX Design System & Frontend Engineering Skill

## 1. Design Philosophy & Aesthetic

- **Visual Identity:** Linear/Vercel-inspired high-precision SaaS aesthetic. Dark-mode primary workspace with high-contrast text, subtle 1px border lines, and frosted glass navigation.
- **Surface Elevation & Glassmorphism:**
  - Floating headers/toolbars: `bg-background/80 backdrop-blur-md border-b border-border/40`.
  - Workspace background: Deep neutral zinc/slate (`bg-zinc-950`).
  - Active editor canvas: Utilitarian matte background (`bg-zinc-950/40`).
  - Paper preview canvas: Muted neutral desk background (`bg-zinc-900/60`) housing a simulated sheet of paper with physical drop elevation (`shadow-2xl`).

---

## 2. Layout & Spatial Architecture

- **Structure:** Full-height application view (`h-screen overflow-hidden flex flex-col`).
- **Header/Toolbar:** Compact sticky top navigation bar (height: 56px / `h-14`) housing branding, document format settings, theme toggle, and export actions.
- **Main Viewport (Split-Pane Architecture):**
  - **Desktop (>= 1024px):** Exactly 50/50 two-column split (`grid grid-cols-2 flex-1 overflow-hidden`).
  - **Mobile/Tablet (< 1024px):** Vertically stacked layout (`grid grid-cols-1 overflow-y-auto`).
  - **Left Pane (The Input Engine):**
    - Sub-header with document mode tabs (`Markdown` vs. `Raw HTML`) and character/word counter.
    - Full-height raw code editor textarea with zero border outline, subtle scrollbars, and `font-mono text-sm leading-relaxed`.
  - **Right Pane (The Tangible Paper Canvas):**
    - Scrollable interactive desk environment (`overflow-y-auto p-8 flex justify-center items-start`).
    - Physical paper simulation sheet centered horizontally.

---

## 3. Paper Simulation Specifications

- **Dimensions & Ratios:**
  - **A4 Portrait:** `w-full max-w-[210mm] min-h-[297mm]`
  - **A4 Landscape:** `w-full max-w-[297mm] min-h-[210mm]`
  - **Letter Portrait:** `w-full max-w-[216mm] min-h-[279mm]`
  - **Letter Landscape:** `w-full max-w-[279mm] min-h-[216mm]`
  - **Legal Portrait:** `w-full max-w-[216mm] min-h-[356mm]`
  - **Legal Landscape:** `w-full max-w-[356mm] min-h-[216mm]`
- **Paper Theming:**
  - **Light Theme:** `bg-white text-zinc-900 prose-zinc`
  - **Dark Theme:** `bg-slate-900 text-slate-100 prose-invert`
- **Typography & Prose:**
  - Styled with `@tailwindcss/typography` using `prose max-w-none`.
  - Headers (`h1`, `h2`, `h3`) with tight letter spacing (`tracking-tight`) and strong weights (`font-bold`).
  - Tables styled with clean 1px borders, subtle alternating row backgrounds, and padding.
  - Code blocks wrapped in syntax highlighters with rounded corners (`rounded-md`) and inset padding.

---

## 4. Component Rules & Micro-Interactions

- **ShadCN UI Standards:**
  - All interactive dropdowns (`Select`), sliders (`Slider`), and tabs (`Tabs`) must use compact heights (`h-8 text-xs`).
  - Primary Export Button:
    - Default state: High-contrast primary action with `lucide-react` download icon.
    - Active/Generating state: Disabled state with animated spinner (`Loader2 className="animate-spin"`), cursor lock, and dynamic label change (`Exporting...`).
- **Margins & Sliders:**
  - Margin slider dynamically updates the internal padding of the preview paper in millimeters (`0mm` to `25mm`).
- **Animations & Transitions:**
  - Tab switches: Instantaneous text swap with smooth fade-in.
  - Theme toggle: Smooth background transition (`transition-colors duration-200`).
