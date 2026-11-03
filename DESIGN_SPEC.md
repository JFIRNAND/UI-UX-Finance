# KaitoFin — Design System & Figma Specification
## Version 1.0 · November 2026 · Greenfield Redesign

---

## PROJECT OVERVIEW

**Product:** KaitoFin / Kaito Finance  
**Category:** AI-powered personal and business financial management  
**Target Users:** University students, freelancers, UMKM owners  
**Key Differentiator:** AI receipt scanning + natural language transaction input  
**Figma File:** https://www.figma.com/design/VIjcojtMBtt9fYz2IzYRh3/Kaito-FIn?node-id=0-1

---

## FIGMA PAGE STRUCTURE TO CREATE

| Page | Purpose |
|------|---------|
| `00 — Design Brief & References` | Product context, reference mapping, design principles |
| `01 — Design System` | Color variables, typography, spacing, components |
| `02 — Landing Page` | Desktop 1440px + tablet 1024px + mobile 390px |
| `03 — Personal Workspace` | Dashboard, KPI, AI input, transaction list |
| `04 — Business Workspace` | Business dashboard (visually distinct from personal) |
| `05 — Receipt Scanning & AI Input` | 8 states: Upload → Preview → Processing → Extraction → Edit → Confirm → Success → Error |
| `06 — Transaction Review & Confirmation` | Smart confirmation modal, edit form |
| `07 — Financial Analytics & Budget` | Charts, category breakdown, period comparison |
| `08 — Subscription & Upgrade PRO` | Quota status, 3-step upgrade flow |
| `09 — Admin Dashboard` | User management, quota allocation, upgrade verification |
| `10 — Responsive Design` | Mobile 390px versions of key screens |
| `11 — Prototype & User Flows` | Connection map for 6 flows |

---

## DESIGN SYSTEM

### COLOR TOKENS

```
Brand / Core
--brand-primary:      #1A2E2B  (deep forest charcoal)
--brand-secondary:    #2D4A45  (muted teal-forest)
--brand-accent:       #1E9E7E  (restrained teal — CTA ONLY)
--brand-accent-dark:  #17826A  (teal hover)
--brand-accent-light: #E6F7F3  (teal subtle background)
--brand-accent-muted: #B3E8DC  (teal muted)

Surfaces (elevation via lightness, NOT shadows)
--surface-page:     #F7F5F1  (warm parchment)
--surface-card:     #FFFFFF  (card backgrounds)
--surface-elevated: #FDFCFA  (slightly elevated)
--surface-inset:    #F0EDE7  (recessed sections)
--surface-dark:     #1A2E2B  (inverse dark sections)

Typography
--text-primary:   #12201D
--text-body:      #2C3D39
--text-secondary: #4A6259
--text-muted:     #7A938D
--text-on-dark:   #F0EDE7
--text-on-dark-2: #A8C5BD
--text-on-accent: #FFFFFF

Borders
--border-default: #D8D3CB
--border-muted:   #E8E4DD
--border-focus:   #1E9E7E  (teal focus ring)
--border-strong:  #B0AAA0

Semantic (financial meaning)
--income-color:   #15803D  income / positive
--income-bg:      #F0FDF4
--expense-color:  #B91C1C  expense / negative
--expense-bg:     #FEF2F2
--warning-color:  #B45309
--warning-bg:     #FFFBEB
--ai-color:       #0D7A6B
--ai-bg:          #E6F7F3
--ai-border:      #99DDD0
```

**BANNED COLORS:** Purple (#6366f1, #8B5CF6, #A855F7), indigo, pink-to-purple gradients, neon glows

### TYPOGRAPHY

**Display Font:** Bricolage Grotesque (headings, page titles, large numbers)  
**Body Font:** IBM Plex Sans (body text, UI labels, form inputs)  
**Mono Font:** IBM Plex Mono (code, financial account numbers)

**Financial numbers:** Always `font-variant-numeric: tabular-nums` + `font-feature-settings: "tnum" 1, "zero" 1`

**Scale (Major Third 1.25):**
```
text-xs:   12px  (labels, captions, badges)
text-sm:   14px  (body secondary, metadata)
text-base: 16px  (body primary, inputs)
text-lg:   20px  (card titles, section labels)
text-xl:   25px  (page headings, KPI values)
text-2xl:  31px  (section headings)
text-3xl:  39px  (hero KPI values)
text-4xl:  49px  (display numbers, step numbers)
```

**Per-role rules:**
- Headings: font-weight 700-800, line-height 1.1-1.2, tracking -0.025 to -0.04em
- Body: font-weight 400, line-height 1.5-1.625
- KPIs: font-weight 600-700, tabular-nums, tracking -0.02em
- Labels: font-weight 500-600, uppercase allowed only for small metadata

### SPACING SCALE (8px base)
```
4px   8px   12px   16px   20px   24px   32px   40px   48px   64px   80px   96px
```

### RADIUS SCALE (differentiated, never uniform)
```
radius-sm:   4px   (badges, chips, small inputs)
radius-md:   8px   (buttons, inputs, nav items)
radius-lg:   12px  (cards, panels, sections)
radius-xl:   16px  (modals, large cards)
radius-2xl:  24px  (hero elements, hero dashboard preview)
radius-full: 9999px (pills, avatars, workspace badges)
```

### SHADOW HIERARCHY
```
Cards:    0 1px 3px 0 rgb(26 46 43 / 0.06) + 0 2px 8px 0 rgb(26 46 43 / 0.04)
Floating: 0 8px 24px 0 rgb(26 46 43 / 0.10)  (dropdowns, popovers)
Modal:    0 16px 40px 0 rgb(26 46 43 / 0.12)
NO shadow on cards — use border only. Shadow reserved for floating elements.
```

---

## SCREEN SPECIFICATIONS

### 02 — LANDING PAGE (1440px)

**Sections in order:**
1. **Navbar** (fixed, 64px): Logo left, nav links center, quota badge + CTA right
2. **Hero** (split, left-aligned): Text left 1.15fr / product screenshot right 1fr
   - Headline: "Catat keuangan / cukup foto struk / atau ketik santai"
   - Subhead: product description
   - Primary CTA: "Coba Scan Struk Gratis" (filled teal)
   - Secondary: "Lihat cara kerja" (outlined)
   - Hero visual: Dark dashboard frame showing balance card, stats, AI input, transactions
3. **Feature Strip** (dark band): 4 features with teal icon squares
4. **Features** (non-uniform grid): 6 cards — AI Receipt (wide, dark bg), NLP, Dual Workspace, Smart Confirm, Analytics, Freemium
5. **How It Works** (warm background): 4 numbered steps, large step numbers in border color
6. **Workspace** (2-col): Personal (light card) vs Business (dark card) — visually distinct
7. **Pricing** (2-col): Free + PRO, no gradient rings, PRO uses dark bg fill
8. **CTA** (full-width dark): Centered heading, body, 2 CTAs
9. **Footer** (minimal): Logo + copyright left, 4 real links right

### 03 — PERSONAL DASHBOARD (1440px with sidebar)

**Shell:** 56px fixed header + 256px sidebar + scrollable main  
**Sidebar:** Workspace switcher (Personal | Bisnis) + nav items + user footer  
**Active nav style:** subtle teal background (`#E6F7F3`), teal icon, medium weight text

**Content sequence:**
1. Page title + CTA button row
2. **Balance card** (dark gradient, full width): Saldo, period, quick action buttons
3. **KPI row** (4-up): Pemasukan, Pengeluaran, Saldo bulan ini, Transaksi count
4. **AI Quick Input**: Input field + Scan shortcut + example chips
5. **Dashboard grid** (2-1 split): Bar chart (income vs expense) + Category breakdown
6. **Budget progress**: 3 budget items with progress bars
7. **Recent transactions**: List with icon, name, metadata, amount

**Personal visual identity:**
- Warm parchment page background
- Teal accent throughout
- Balance card: forest charcoal gradient

### 04 — BUSINESS DASHBOARD (1440px with sidebar)

**Visually distinct from Personal:**
- Balance card: Dark navy gradient (NOT forest green)
- Blue accent (not teal) for business expense bars
- "UMKM & Bisnis" badge visible
- Sidebar: Business tab active
- Different category colors (Blue instead of teal for costs)
- Warning banner at bottom: "Data bisnis ini sepenuhnya terpisah"

### 05 — RECEIPT SCANNING (full page)

**8 states, all required:**

**State 1 — Upload Zone:**
- Large dashed border zone (2px dashed #D8D3CB)
- Upload icon (teal background)
- "Seret foto struk ke sini" title
- File format chips: JPG PNG WEBP Max 10MB
- "atau" divider with lines
- "Ambil Foto dengan Kamera" secondary button

**State 2 — Preview:**
- 2-col: Receipt preview (monospace mock) + action panel
- "Proses dengan AI" primary button (shows -1 kuota cost)
- "Yang akan diekstrak AI" info card (teal bg)
- Cancel option

**State 3 — AI Processing:**
- Centered spinner ring (teal, 72px)
- "AI sedang membaca struk kamu..." title
- 4 processing steps with status dots (done/active/pending)
- Subtle progress indication

**State 4 — Extraction Result:**
- 2-col: Receipt preview + Editable form
- Alert banner: "AI berhasil mengekstrak..." (teal)
- Form fields with "Diekstrak AI" chips
- Confidence badge: "97% yakin"
- Type toggle: Pengeluaran / Pemasukan
- All fields editable: Nominal, Deskripsi, Tanggal, Kategori, Catatan
- "Konfirmasi & Simpan" primary + "Batal" secondary

**State 5 — Success:**
- Centered success icon (green circle, checkmark)
- Transaction confirmed details
- "Scan Struk Lagi" + "Kembali ke Dashboard" actions

**State 6 — Error:**
- Centered error icon (red)
- Error message
- "Coba Lagi" + "Input Manual" actions

**NLP Mode:**
- Large textarea input (2px border, xl radius)
- Example cards (4, 2-col grid) — each shows input text + parsed result preview
- AI parsing result section (same extraction form pattern)

### 06 — TRANSACTION CONFIRMATION MODAL

**Modal specs (480px max-width):**
- Header: "Konfirmasi Transaksi" + X close button
- Transaction summary card (amount prominent)
- Detail rows: tanggal, toko/deskripsi, kategori, workspace
- Warning: "Transaksi tidak dapat dibatalkan setelah dikonfirmasi"
- Footer: "Batal" (secondary) + "Simpan Transaksi" (primary)
- Anti double-submit: button disables after first click, shows spinner

### 07 — FINANCIAL ANALYTICS

**Screens:**
1. Period selector tabs (7H / Bulan Ini / 3 Bulan / Tahun Ini)
2. 3-col summary (Pemasukan / Pengeluaran / Saldo Bersih)
3. Trend line chart (SVG, teal, gradient fill, no axes)
4. 2-col: Spending categories (horizontal bars) + Income sources
5. Month comparison (3 cards, current highlighted with teal)

### 08 — UPGRADE PRO

**Screens:**
1. Quota status bar (warning yellow, shows 8/10)
2. PRO benefits card (dark background, gradient badge)
3. 3-step process:
   - Step 1: Bank transfer details + copy button
   - Step 2: WhatsApp confirmation + message template
   - Step 3: Admin verification & quota allocation
4. Status note (teal info banner)

### 09 — ADMIN PANEL

**Screens:**
1. Admin KPI row: Total Users, PRO Users, Pending Upgrades
2. Pending upgrades table (warning amber): user, status, quota input + approve/reject
3. All users table: avatar, name, email, AI quota (editable), status badge, save button
4. Admin note at bottom

---

## COMPONENT LIBRARY (Figma Components to Build)

### Atoms
- Color swatches (all tokens)
- Typography specimens
- Spacing scale
- Radius scale
- Shadow examples

### Buttons
- Primary (filled teal)
- Secondary (outlined)
- Ghost
- Destructive
- Icon-only
- All states: default, hover, focus, disabled, loading

### Badges / Chips
- Income (green)
- Expense (red)
- Warning (amber)
- AI (teal)
- Neutral (gray)
- PRO (gradient)

### Form Controls
- Text input (default, focus, error, success)
- Select / dropdown
- Textarea
- Toggle (type selector: Pengeluaran | Pemasukan)
- File upload zone

### Cards
- Standard card (border only)
- Interactive card (hover shadow)
- Dark card (dark bg)
- Highlight card (teal bg)
- KPI stat card
- Feature card

### Navigation
- Sidebar nav item (default, active, hover)
- Workspace switcher
- Header breadcrumb
- Period tab
- Mode selector tab (scan vs NLP)

### Data Display
- Transaction row
- Category bar
- Budget progress bar
- Sparkline (mini area chart)
- AI extraction chip
- Quota indicator

### Overlays
- Confirmation modal
- Toast (success, error, info)
- Processing ring + steps

---

## PROTOTYPE FLOWS

### Flow A — Main Navigation
`Landing Page → "Mulai Gratis" → Dashboard Personal`

### Flow B — Receipt Scanning (Full)
`Dashboard → "Scan Struk" → Upload State → Click zone → Preview → "Proses dengan AI" → Processing State → Extraction State → Edit form → "Konfirmasi & Simpan" → Confirmation Modal → "Simpan" → Success State → "Kembali ke Dashboard"`

### Flow C — Natural Language Input
`Dashboard → AI input field → Type text → "Parse dengan AI" → NLP Result → Edit → "Konfirmasi & Simpan" → Success`

### Flow D — Workspace Switching
`Personal Dashboard → Click "Bisnis" tab → Business Dashboard → Click "Personal" tab → Personal Dashboard`  
Visual difference: dark navy balance card, blue cost bars, business badge, warning note

### Flow E — PRO Upgrade
`Dashboard → "Upgrade PRO" nav item → Upgrade page → See quota status → Steps → WA button`

### Flow F — Analytics
`Dashboard → "Analitik" nav → Period tabs → Category drill-down → Month comparison`

---

## RESPONSIVE BREAKPOINTS

| Breakpoint | Width | Changes |
|-----------|-------|---------|
| Mobile | 390px | Sidebar hidden, bottom-level navigation, stacked KPIs, hero stacks |
| Tablet | 1024px | Sidebar collapsible (icon rail), 2-col KPIs |
| Desktop | 1440px | Full sidebar, 4-col KPIs, full dashboard grid |

**Mobile-specific patterns:**
- Sidebar → slide-out drawer (hamburger trigger)
- Balance card: full-width, stacked actions
- KPI row: 2×2 grid
- Hero: stacks vertically, product visual moves above text
- Pricing: single column
- Features: single column

---

## ANTI-SLOP VERIFICATION

✅ No purple/indigo as primary color (using forest teal #1E9E7E)  
✅ No gradient text (solid high-contrast headlines only)  
✅ No `border-l-4 border-purple` left-accent cards  
✅ No glassmorphism navbar (solid white, 1px border-b)  
✅ No emoji icons (all SVG)  
✅ No `hover:scale-105` (using hover:shadow-md/border-color transitions)  
✅ No fake "Trusted by 5,000+" logos  
✅ No "Supercharge/Unlock/Seamless" copy  
✅ No generic "Get Started" CTA (using "Coba Scan Struk Gratis")  
✅ No uniform `rounded-2xl` everywhere (differentiated radius scale)  
✅ No aurora/blob backgrounds  
✅ No uniform 3-card feature grid (mixed sizes with wide card)  
✅ Body text ≥ gray-700 equivalent (#2C3D39 = very good contrast)  
✅ `prefers-reduced-motion` respected in animations  
✅ All interactive elements use `<button>` or `<a>`  
✅ Financial numbers always `tabular-nums`  
✅ WCAG AA contrast verified for primary text/background pairs  

---

## FEATURES FROM SOURCE CODE (Verified)

Based on the KaitoFin website and product description:

| Feature | Implemented | Notes |
|---------|-------------|-------|
| AI Receipt OCR (Gemini) | ✅ Yes | Scan struk, extract nominal/toko/kategori |
| Natural Language Input | ✅ Yes | "Beli nasi padang 25rb" |
| Personal Workspace | ✅ Yes | Separate from business |
| Business Workspace | ✅ Yes | UMKM isolation |
| Freemium (10x AI) | ✅ Yes | Free quota |
| PRO upgrade (WA transfer) | ✅ Yes | Manual admin verification |
| Admin Panel | ✅ Yes | Quota allocation (Dava Rafael) |
| Smart Confirmation Modal | ✅ Yes | Anti double-submit |
| PostgreSQL Persistent | ✅ Yes | Not in-memory |
| Transaction review | ✅ Yes | Review before save |

**Discrepancies / Not in scope:**
- Investment trading: NOT a feature (correctly excluded)
- Cryptocurrency: NOT a feature (correctly excluded)
- Real-time dashboard with live data: Design is static mockup

---

## NEXT STEPS FOR FRONTEND IMPLEMENTATION

1. **Set up design tokens** in CSS/Tailwind from `src/styles/tokens.css`
2. **Configure fonts**: Add IBM Plex Sans + Bricolage Grotesque to `_app.tsx` or `layout.tsx`
3. **Component library**: Build atoms from `src/styles/components.css`
4. **Connect Gemini AI**: Receipt scanning → `app/api/scan/route.ts`
5. **Auth system**: Login/register flows (not yet designed — add auth pages)
6. **Database schema**: Map transaction fields from extraction form
7. **Responsive CSS**: Apply `@media` breakpoints from token definitions
8. **Figma → Code Connect**: Connect Figma components to React components

---

*Generated by KaitoFin Redesign Project · Kiro AI IDE · November 2026*
