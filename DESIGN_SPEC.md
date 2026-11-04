# KaitoFin — Competition-Grade UI/UX Design Specification
## Version 2.0 · November 2026 · Mobile Redesign

---

## 1. DESIGN THINKING FOUNDATION

### Problem Statement
Mahasiswa, freelancer, dan UMKM di Indonesia kesulitan melacak arus kas karena aplikasi
keuangan yang ada terlalu kompleks, menggunakan bahasa asing, atau tidak memahami
keunikan kebutuhan mereka (dual income source, cash-based transactions, campur-aduk
keuangan pribadi dan bisnis).

### Empathy Map (3 User Personas)

#### Persona 1 — Mahasiswa (Primary)
| | Says | Thinks | Does | Feels |
|---|---|---|---|---|
| Pain | "Duitnya habis tapi ga tau ke mana" | "Susah inget pengeluaran harian" | Bayar kontan, jarang transfer | Cemas soal keuangan akhir bulan |
| Gain | "Kalau ada yang bisa scan struk" | "Pengen pisahin uang jajan &amp; tabungan" | Beli makan 3× sehari | Lega kalau tau saldo cukup |

**Job-to-be-done:** Lacak uang saku tanpa ribet, tau kapan harus hemat.

#### Persona 2 — UMKM (Warung/Toko Online)
| | Says | Thinks | Does | Feels |
|---|---|---|---|---|
| Pain | "Omset keliatan banyak tapi ga tau untung/rugi" | "Susah pisahin duit belanja bahan dan duit pribadi" | Bayar supplier kontan, catat manual di buku | Overwhelmed ngurus keuangan |
| Gain | "Mau tau laba bersih tiap bulan" | "Kalau ada aplikasi yang ngerti UMKM" | Scan nota bahan baku | Confident soal keputusan bisnis |

**Job-to-be-done:** Lacak omset vs biaya operasional, hitung laba bersih.

#### Persona 3 — Freelancer
| | Says | Thinks | Does | Feels |
|---|---|---|---|---|
| Pain | "Income ga tetap, susah budgeting" | "Harus pisahin proyek A dan B" | Transfer masuk dari berbagai klien | Stres saat freelance sepi |
| Gain | "Mau tau total income per klien/proyek" | "Pengen tracking invoice yang sudah dibayar" | Catat pemasukan pas gajian | Senang kalau proyek banyak |

**Job-to-be-done:** Rekap pemasukan per klien, pantau rasio saving.

---

## 2. DESIGN PRINCIPLES APPLIED

### Nielsen's 10 Usability Heuristics (Mapping)
| # | Heuristic | Implementation in KaitoFin |
|---|---|---|
| 1 | Visibility of system status | AI Quota badge selalu visible di header; processing ring dengan step indicator |
| 2 | Match system &amp; real world | Bahasa Indonesia; "Struk" bukan "receipt"; "Uang Saku" bukan "allowance" |
| 3 | User control &amp; freedom | Cancel di setiap state scan; Batal di confirmation; back arrow di semua sub-pages |
| 4 | Consistency &amp; standards | Radius scale tetap: btn 16px, card 18-24px, modal 24px; warna teal selalu = tindakan |
| 5 | Error prevention | Smart confirmation modal sebelum save; "Review &amp; Koreksi" sebelum AI process |
| 6 | Recognition over recall | Transaction list selalu visible; badge AI + kategori di setiap transaksi |
| 7 | Flexibility &amp; efficiency | 2 metode input (scan + NLP); shortcut FAB di bottom nav |
| 8 | Aesthetic &amp; minimalist design | Dark surfaces, teal single accent, no decorative gradients on text |
| 9 | Help users recognize/recover from errors | Error state dengan ikon jelas + "Coba Lagi" + "Input Manual" fallback |
| 10 | Help &amp; documentation | In-context tips: AI extracted chips, confidence badge, "Yang akan diekstraksi" panel |

### Shneiderman's 8 Golden Rules
1. **Strive for consistency** — Workspace pill, card style, icon set (custom SVG, stroke 1.4–1.6px) konsisten di semua halaman
2. **Enable frequent users** — FAB center untuk aksi utama; scan tersedia dari dashboard tanpa navigasi
3. **Offer informative feedback** — AI processing step dots, confidence badge "97% yakin", success state dengan amount
4. **Design dialogs for closure** — Upload → Preview → Processing → Extraction → Confirm → Success (6-state flow dengan jelas)
5. **Prevent errors** — Confirmation modal anti double-submit, type toggle jelas pengeluaran/pemasukan
6. **Permit easy reversal** — Batal di setiap langkah, "Ganti Foto" tersedia, back button always present
7. **Support internal locus of control** — User selalu konfirmasi sebelum save; AI tidak pernah otomatis simpan
8. **Reduce short-term memory load** — AI extracted chip menampilkan data dari struk inline dengan form field

### The 7 Principles of Universal Design — Ronald Mace
1. **Equitable use** — Tersedia gratis (10 AI quota); tidak diskriminasi berdasarkan device
2. **Flexibility in use** — 2 mode input (scan foto + teks natural); iOS &amp; Android friendly
3. **Simple &amp; intuitive** — 4 quick action tombol; bottom nav 5 item dengan label
4. **Perceptible information** — High contrast text (#EDE9E0 on dark, WCAG AA+); icon + label di nav
5. **Tolerance for error** — Review state wajib; tidak ada auto-save; cancel selalu tersedia
6. **Low physical effort** — 48px minimum touch targets; FAB di center bottom nav (thumb zone)
7. **Size &amp; space for approach** — Mobile-first 390px; card padding 18-22px; baris transaksi min-height 70px

---

## 3. DESIGN SYSTEM TOKENS

### Color Palette (60-30-10 Rule)

**60% — Background Surfaces (Forest Dark)**
```
--surface-bg:       #0A1410   Page background
--surface-card:     #152420   Card background  
--surface-elevated: #1A2E28   Elevated card
--surface-dark:     #0F2821   AI advisor card
```

**30% — Typography & Borders**
```
--text-primary:     #EDE9E0   Body text (ratio: 13.5:1 on --surface-bg)
--text-body:        #C8D8D4   Secondary text (ratio: 8.2:1)
--text-secondary:   #8AADA6   Muted text (ratio: 4.9:1 — WCAG AA)
--text-muted:       #6A8C84   Caption text
--text-disabled:    #3E5C55   Disabled / meta
--border-default:   rgba(255,255,255,0.07)
--border-focus:     #1E9E7E   Focus ring
```

**10% — Accent & Semantic**
```
--brand-teal:       #1E9E7E   Primary CTA, active states
--brand-teal-light: #2BBFA0   Hover, links, badges
--brand-teal-dark:  #17826A   Pressed states

--income:           #52E39A   Income amounts
--expense:          #FF7B7B   Expense amounts
--invest:           #7AB8FF   Investment
--warning:          #FFBE55   Warning, quota
--pro:              #C4AAFF   PRO features
```

### Typography System (Bricolage Grotesque + IBM Plex Sans)
```
Display/Heading:  Bricolage Grotesque — expressive, editorial, warm authority
Body/UI:          IBM Plex Sans — clean, humanist, technical precision
Mono/Code/Nominals: IBM Plex Mono — receipt preview, account numbers
```

**Type Scale (Major Third 1.25×)**
```
10px  — disabled captions
11px  — metadata, timestamps, badges  ← minimum for content
12px  — secondary body, labels
13px  — nav labels, helper text
14px  — body secondary, descriptions
15px  — body primary, input values
16px  — form inputs (browser zoom prevention)
18px  — brand name, large labels
19px  — page titles
21px  — workspace title
24px  — section headings, login title
26px  — landing section titles
32px  — amount emphasis  
36px  — balance hero (primary KPI)
```

### Spacing (8px Grid)
```
4px   — gap between inline elements
8px   — gap between related items  
10px  — card gap in grid
12px  — within-card gap
14px  — transaction row padding
16px  — section labels margin
18px  — card padding (compact)
20px  — horizontal page margin
22px  — landing padding
24px  — balance card padding, section titles
28px  — major section gaps
```

### Radius Scale (Differentiated — not uniform)
```
5px   — tags, micro badges
6px   — status badges
8px   — small chips, code snippets  
10px  — bottom nav items, logo (32px)
11px  — logo (36px)
12px  — icon buttons, scan mode tabs
14px  — small buttons (secondary)
16px  — form inputs, workspace tabs
18px  — standard cards
20px  — KPI cards
22px  — chart cards, large cards
24px  — workspace cards, pricing cards, CTA
28px  — hero phone mockup
44px  — avatar (50%)
```

### Elevation System (Surface Tints — Not Shadows)
```
Layer 0  — #0A1410  (page bg)
Layer 1  — #152420  (standard card)
Layer 2  — #1A2E28  (elevated card, slightly lighter)
Layer 3  — #1E3530  (highlighted/featured)
Layer 4  — #264840  (balance hero)
Floating — box-shadow: 0 8px 32px rgba(0,0,0,0.4)  (modals only)
```

---

## 4. COMPONENT CATALOG

### Buttons
| Variant | Size | Usage |
|---|---|---|
| Primary (teal gradient) | 52px height, 16px radius | One per screen — main CTA |
| Secondary (ghost) | 52px height, 16px radius | Cancel, back, secondary |
| Ghost (transparent) | 36px min-height | Nav items, text actions |
| FAB (center bottom nav) | 52×52px, 17px radius | Primary mobile action |
| Quick Action | 80px min-height, 18px radius | Dashboard shortcuts |

### Cards
| Type | Border-radius | Padding | Usage |
|---|---|---|---|
| KPI Card | 20px | 18px 16px | 2×2 grid metrics |
| Chart Card | 22px | 18px 20px | Donut/bar charts |
| AI Advisor | 22px | 18px | Tips grid, full width |
| Txn List | 22px | container | Transaction rows |
| Feature Card | 22px | 22px | Landing features |
| Balance Hero | 24px | 24px 22px | Main balance display |
| Workspace Card | 24px | 22px | Personal/Business compare |

### Navigation
- **Bottom Nav**: 5 items, FAB center, 52px touch targets, 10px icon size, 10px label
- **Workspace Pill**: 2 tabs, 14px radius, active = teal gradient, 9px padding
- **Sticky Landing Nav**: blur(16px) backdrop, 1px bottom border, 36px button height

---

## 5. SCREEN SPECIFICATIONS (Mobile 390px)

### Screen 1: Landing Page
**Sections sequence (different anatomy each):**
1. Sticky Nav — logo + 3 links + CTA button
2. Hero — centered headline + trust badge + phone mockup below
3. Feature Strip — horizontal scroll pills
4. Features — wide dark card + 2×2 grid cells
5. How It Works — numbered list + teal connector line
6. Workspace Comparison — personal (teal) vs business (blue) cards
7. Pricing — 2 stacked cards (fill differentiation, not rings)
8. CTA — dark teal card, centered copy, 2 actions
9. Footer — logo + copyright + 4 real links

### Screen 2: Login Page
- Branding hero (50% height) with logo + tagline
- Form section: email, password (toggle show/hide), submit
- Demo shortcut button
- Register link
- Back to landing link

### Screen 3: Personal Dashboard
**Hierarchy:**
1. Status bar + App header (brand + quota + notif + avatar)
2. Workspace pill switcher
3. Workspace label bar (badge + title + desc + quota status)
4. Balance Hero Card (36px amount, mini stats)
5. Quick Actions (4 buttons)
6. KPI Grid 2×2 (income/expense/flow/invest)
7. Donut Chart Card (with period tabs)
8. AI Advisor Card (3-col tips grid)
9. Transaction List (filter + 3 rows)
10. Bottom Navigation (5 items + FAB)

### Screen 4: Business Dashboard
Identical structure to Personal but:
- App background: #0D1520 (navy bias)
- Balance hero: navy gradient, blue border
- Workspace pill: blue active state
- Workspace label badge: blue (#7AB8FF)
- KPI labels: Omset, HPP, Laba Bersih
- AI Advisor: UMKM-specific tips (pisahkan rekening, efisiensi operasional)
- Warning note: "Data bisnis sepenuhnya terpisah dari Personal"

### Screen 5: Scan / AI Input
**Modes:** Scan Struk | Input Cepat (toggle)

**Scan Flow (6 states):**
1. **Upload** — dashed upload zone + camera button + AI extraction preview
2. **Preview** — receipt mock + process button (-1 quota notice)
3. **Processing** — spinner ring + 4 step dots with labels
4. **Extraction** — AI alert + receipt + editable form (type toggle, amount, desc, date, category, workspace, notes)
5. **Success** — icon + title + amount + 2 actions
6. **Error** — icon + message + retry + manual fallback

**NLP Flow:**
- Large textarea + Parse button
- 4 example cards (2×2 grid)
- Result form (same extraction pattern)

### Screen 6: Analytics
- Period tabs (4 options)
- 3-col summary KPIs
- Bar chart (6-month comparison)
- Category breakdown (progress bars)
- 3-month comparison cards

### Screen 7: Upgrade PRO
- Quota status bar (amber warning)
- PRO benefits card
- 3-step flow (Transfer → WhatsApp → Verify)
- Info note

---

## 6. WIREFRAME ANNOTATIONS

### Dashboard Wireframe (Lo-fi)
```
┌─────────────────────────────────┐
│ ●●●  Status Bar  09:41    ∎▲▮  │ ← 48px
├─────────────────────────────────┤
│ [K] KaitoFin        8/10 🔔 DR │ ← 56px, brand + quick status
│                                 │
│ [ Personal ──────│ Bisnis(UMKM)]│ ← workspace switcher pill
├─────────────────────────────────┤
│ [PERSONAL WORKSPACE] Gratis     │
│ Keuangan Pribadi & Mahasiswa    │ ← workspace label, 2-col
│ Kelola uang saku...    7/10 ↑  │
├─────────────────────────────────┤
│ ┌───────────────────────────┐   │
│ │ • Total Saldo · Personal  │   │ ← balance hero card
│ │  Rp 3.450.000             │   │   36px amount
│ │  Per 3 Nov 2026           │   │
│ │ [+Rp5.2jt] [-Rp1.75jt]   │   │ ← mini stats 2-col
│ └───────────────────────────┘   │
├─────────────────────────────────┤
│ [📷Scan] [✏Input] [📊Ana] [⭐Pro] │ ← quick actions 4-up
├─────────────────────────────────┤
│ Ringkasan Keuangan    Lihat →   │
│ ┌─────────┐ ┌─────────┐        │
│ │↑Pemasuk │ │↓Keluar  │        │ ← KPI 2×2 grid
│ │Rp3.9jt  │ │Rp415k   │        │
│ │+12% Okt │ │+8% Okt  │        │
│ └─────────┘ └─────────┘        │
│ ┌─────────┐ ┌─────────┐        │
│ │ArusKas  │ │Investasi│        │
│ │Rp3.485k │ │Rp200k   │        │
│ │89% ratio│ │Terlacak │        │
│ └─────────┘ └─────────┘        │
├─────────────────────────────────┤
│ Visualisasi Distribusi          │
│ ┌─────────────────────────────┐ │
│ │ [Keluar][Masuk][Portofolio] │ │ ← period tabs
│ │                             │ │
│ │    ○ donut     ─ legend     │ │ ← chart
│ │                             │ │
│ └─────────────────────────────┘ │
├─────────────────────────────────┤
│ ┌─────────────────────────────┐ │
│ │ AI Advisor  [Arus Kas Sehat]│ │
│ │ [11%│50/30/20│Invest▸]      │ │ ← 3-col tips
│ └─────────────────────────────┘ │
├─────────────────────────────────┤
│ Riwayat Transaksi     Semua →   │
│ ┌─────────────────────────────┐ │
│ │  [♟] Bibit Reksadana        │ │
│ │       Portofolio · Personal │ │ ← transaction rows
│ │                  +Rp200k   │ │
│ │─────────────────────────────│ │
│ │  [↓] MyTelkomsel            │ │
│ │       AI · Tagihan          │ │
│ │                  -Rp95k    │ │
│ └─────────────────────────────┘ │
├─────────────────────────────────┤
│ [🏠Beranda][📊Ana][  +  ][⟺Txn][👤Akun]│ ← bottom nav
└─────────────────────────────────┘
```

---

## 7. PROTOTYPE FLOWS

### Flow A — Onboarding
```
Landing → "Mulai Mengatur" → Login → Dashboard Personal
```

### Flow B — Scan Receipt (Full, 6 states)
```
Dashboard → FAB (+) → scan.html →
[Upload] → tap zone → [Preview] → "Proses dengan AI" →
[Processing] → 3 step dots → [Extraction] → edit form →
"Konfirmasi & Simpan" → [Success] → "Kembali ke Dashboard"
```

### Flow C — Natural Language Input
```
Dashboard → FAB (+) → scan.html#nlp →
[NLP Input] → ketik teks → "Parse dengan AI" →
[NLP Result form] → "Konfirmasi & Simpan" → [Success]
```

### Flow D — Workspace Switch
```
Personal Dashboard → Bisnis tab → Business Dashboard
(visual: navy bg, blue accent, UMKM KPI labels, business transactions)
→ Personal tab → back to Personal Dashboard
```

### Flow E — Upgrade PRO
```
Dashboard → "Upgrade PRO" quick action →
upgrade.html → quota bar → PRO card → 3 steps →
WhatsApp button
```

### Flow F — Analytics Drill-down
```
Dashboard → "Analitik" bottom nav →
analytics.html → period tabs → category breakdown → month comparison
```

---

## 8. ACCESSIBILITY CHECKLIST (WCAG AA)

- [x] `<html lang="id">` on all pages
- [x] All images have `alt` or `aria-hidden`
- [x] All icon-only buttons have `aria-label`
- [x] All forms have visible labels wired to inputs
- [x] Focus rings visible on all interactive elements (`outline: 2px solid #1E9E7E`)
- [x] Color never the only indicator (icons + text labels always pair)
- [x] Minimum touch targets 44-48px
- [x] `prefers-reduced-motion` gated on all animations
- [x] `aria-current="page"` on active nav items
- [x] `role="status"/"region"/"list"/"article"` throughout
- [x] Tabular numerics (`font-variant-numeric: tabular-nums`) on all financial data
- [x] Screen-reader alternative (`<table class="sr-only">`) for donut chart
- [x] `aria-live="polite"` on dynamic states (processing, success)
- [x] `aria-expanded` and `aria-pressed` on toggle buttons

---

## 9. COMPETITION READINESS CHECKLIST

### UI Quality
- [x] Mobile-first 390px viewport
- [x] Phone frame visible on desktop (competition judges view from desktop)
- [x] Dark premium fintech aesthetic — not generic SaaS
- [x] 3-tier surface elevation system (not shadow-everywhere)
- [x] Consistent radius scale (5 / 8 / 12 / 16 / 18 / 20 / 22 / 24 / 28px)
- [x] Bricolage Grotesque display + IBM Plex Sans body — distinctive pairing
- [x] All financial numbers: tabular-nums, letter-spacing -0.02em+

### UX Depth
- [x] Design Thinking documented (empathy map, 3 personas)
- [x] Nielsen 10 heuristics mapped to implementation
- [x] Shneiderman 8 golden rules applied
- [x] Universal Design 7 principles applied
- [x] 6-state scan flow (industry-grade complexity)
- [x] Smart confirmation modal (prevents data errors)
- [x] AI advisor with persona-specific tips
- [x] Dual workspace fully differentiated visually
- [x] Prototype flows documented (A through F)

### Anti-Slop (All P0 violations resolved)
- [x] No purple/indigo accent
- [x] No gradient text
- [x] No `border-l-4` left accents
- [x] No emoji icons
- [x] No glassmorphic nav
- [x] No `hover:scale-105`
- [x] No "Supercharge/Unlock" copy
- [x] No fake "Trusted by X,000+" metrics
- [x] No uniform `rounded-2xl` everywhere
- [x] `prefers-reduced-motion` handled

---

*KaitoFin Design Specification v2.0 · November 2026 · Dava Rafael*
