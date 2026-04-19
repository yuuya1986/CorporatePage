# DESIGN.md — 株式会社エフルム コーポレートサイト

> Japanese UI design contract for AI agents and human reviewers.

---

## 0. Contract Metadata

- **Locale**: `ja-JP`
- **Profile**: `base`
- **Primary writing mode**: `horizontal-tb`
- **Target surfaces**: `web`
- **Review status**: `active`
- **Last reviewed at**: `2026-04-19`
- **Reviewer**: `yuuya1986`

---

## 1. Product Intent

- **What this product is**: 株式会社エフルムのコーポレートサイト（単一ページ）
- **Primary audience**: PSP審査担当者、取引先、事業パートナー
- **Primary usage context**: デスクトップ・モバイルブラウザ
- **Design stance**: 洗練・信頼・清潔感。ITビジネス企業として誠実で有能な印象を与える。
- **Must feel like**: モダンなITスタートアップ。整理されていて、読みやすく、実在感がある。
- **Must not feel like**: 過剰な装飾、アニメーションが多いランディングページ、個人ブログ。

---

## 2. Visual Theme & Brand Signals

- **Keywords**: 信頼・透明性・テクノロジー・つながり・洗練
- **Visual temperature**: `sharp`
- **Density**: `airy`
- **Tone**: フォーマル寄りのプロフェッショナル。親しみはあるが軽くない。
- **Motion stance**: `minimal`

---

## 3. Color System

### Brand colors
- **Primary**: `#1A56DB`（ブルー）
- **Primary hover**: `#1140A8`
- **Accent**: `#1A56DB`

### Semantic colors
- **Success**: `#16A34A`
- **Warning**: `#D97706`
- **Danger**: `#DC2626`
- **Info**: `#0EA5E9`

### Neutral colors
- **Text primary**: `#0F172A`
- **Text secondary**: `#475569`
- **Text muted**: `#94A3B8`
- **Border**: `#E2E8F0`
- **Background**: `#FFFFFF`
- **Surface**: `#F8FAFC`
- **Surface elevated**: `#FFFFFF`

### Color usage rules
- Do not rely on color alone for meaning
- Keep primary actions visually distinct
- Avoid low-contrast muted text on tinted surfaces
- Blue (#1A56DB) is used only for interactive elements and accent; do not overuse as decorative fill

---

## 4. Typography System

### 4.1 Japanese fonts
- **Sans**: `"Hiragino Kaku Gothic ProN"`, `"BIZ UDPGothic"`, `"Noto Sans JP"`
- **Serif**: not used
- **Mono**: not used

### 4.2 Latin fonts
- **Sans**: `Inter`, `system-ui`
- **Serif**: not used
- **Mono**: not used

### 4.3 Fallback policy
```css
font-family: Inter, system-ui, "Hiragino Kaku Gothic ProN", "BIZ UDPGothic", "Noto Sans JP", sans-serif;
```

- Japanese fallback must be explicit
- Font stack must be stable on macOS and Windows
- Avoid leaving Japanese rendering to browser defaults

### 4.4 Type scale

| Role | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|--------|-------------|----------------|------|
| Display | 3rem | 700 | 1.2 | -0.01em | Hero見出し |
| H1 | 2.25rem | 700 | 1.3 | -0.01em | ページ内大見出し |
| H2 | 1.5rem | 600 | 1.4 | normal | セクション見出し |
| H3 | 1.125rem | 600 | 1.5 | normal | カード見出し |
| Body L | 1.0625rem | 400 | 1.8 | normal | 主要本文 |
| Body M | 0.9375rem | 400 | 1.75 | normal | 通常本文 |
| Body S | 0.875rem | 400 | 1.7 | normal | 補足 |
| Caption | 0.75rem | 400 | 1.6 | normal | キャプション・メタ |
| Label | 0.8125rem | 500 | 1.4 | 0.01em | ラベル・ナビ |
| Mono | 0.875rem | 400 | 1.6 | normal | コード（未使用） |

### 4.5 Japanese paragraph rules
- Default Japanese body line-height: `1.75–1.8`
- Default Japanese body letter-spacing: `normal`（本文への過剰なtrackingは禁止）
- Heading and label spacing may differ from body spacing

### 4.6 Mixed-script rules
- 「ANIPIA」「シリヤト!!」などのサービス名は和欧混植になるため、フォントスタック全体で視覚的に検証する
- Avoid visual collision in headings containing English product names
- Do not optimize Latin words in a way that harms Japanese paragraph rhythm

### 4.7 OpenType and rendering
```css
font-kerning: auto;
font-feature-settings: normal;
```

### 4.8 Writing direction
- Default writing direction is horizontal
- Vertical writing is: `not used`

---

## 5. Line Breaking & Overflow

### Default rules
```css
html:lang(ja) {
  line-break: strict;
  word-break: normal;
  overflow-wrap: anywhere;
}
```

### Additional rules
- Do not use global `word-break: break-all`
- Review headings at narrow widths
- Prevent URL overflow without breaking paragraph readability

---

## 6. Layout Principles

- **Container width**: `max-width: 1080px`
- **Reading width**: `max-width: 720px`（本文・説明文）
- **Grid system**: CSS Grid / Flexbox（フレームワーク不使用）
- **Spacing scale**: 4px基準（4, 8, 12, 16, 24, 32, 48, 64, 96px）
- **Section spacing rule**: セクション間は `padding: 96px 0`
- **Whitespace policy**: airy — 要素間に十分な余白を確保し、窮屈な印象を与えない

### Layout rules
- Reading width must prioritize comfort for Japanese paragraphs
- Visual grouping should rely on spacing before borders when possible

---

## 7. Component Guidelines

### Buttons
- Primary button: `background #1A56DB`, `color #FFFFFF`, `border-radius 6px`, `padding 12px 28px`
- Primary hover: `background #1140A8`
- Label length in Japanese must be tested（4〜8文字が理想）

### Cards（サービスカード）
- Border: `1px solid #E2E8F0`
- Border-radius: `8px`
- Padding: `32px`
- Shadow: `0 1px 4px rgba(0,0,0,0.06)`
- Keep title, body, and actions visually separated

### Tables（会社概要）
- Table density must be tuned separately from paragraph density
- `th` は左寄せ、幅固定（180px）
- `td` は本文フォントサイズ、`Body M`

### Navigation
- Mixed Japanese and English labels must be reviewed
- Active state: `color #1A56DB`, underline or border-bottom

---

## 8. Depth, Border, and Surface

### Surface levels
| Level | Usage | Border | Shadow |
|------|------|--------|--------|
| 0 | Page background (#FFFFFF) | none | none |
| 1 | Section surface (#F8FAFC) | none | none |
| 2 | Card | 1px solid #E2E8F0 | 0 1px 4px rgba(0,0,0,0.06) |
| 3 | Header (sticky) | bottom 1px solid #E2E8F0 | none |

### Rules
- Prefer subtle depth
- Avoid decorative shadows that reduce seriousness

---

## 9. Responsive Behavior

- **Breakpoints**: `768px`（mobile/tablet境界）、`1100px`（wide）
- **Mobile reading width**: `100%` with `padding 0 20px`
- **Tablet layout stance**: 1カラムに縮退
- **Desktop layout stance**: 2カラムカード、横並びナビ

### Responsive rules
- Recheck paragraph rhythm on mobile
- Table fallback: モバイルでは `display: block` に変換
- Dense desktop UI must not be copied directly onto mobile

---

## 10. Motion & Interaction

- **Animation stance**: minimal
- **Transition speed**: `200ms ease`
- **Reduced motion policy**: `prefers-reduced-motion: reduce` を尊重

### Rules
- Motion should support hierarchy, not decorate it
- Avoid large shifts that disturb reading

---

## 11. Do's and Don'ts

### Do
- Preserve Japanese reading comfort
- Keep mixed-script text visually balanced（ANIPIA、シリヤト!! 等）
- Review actual line breaks at real widths
- Separate paragraph rules from table rules
- Prefer stable defaults over clever tricks

### Don't
- Do not globalize `word-break: break-all`
- Do not copy Latin-first typography blindly
- Do not increase body letter-spacing without clear reason
- Do not use body line-height that feels compressed for long Japanese text
- Do not accept screenshots alone as final validation

---

## 12. Agent Prompt Guide

Use calm, readable Japanese typography.

Honor the locale and profile before inventing stylistic variations.

Preserve readability first when there is tension between novelty and comfort.

When uncertain:
- keep body text conservative
- keep headings clear
- avoid aggressive spacing
- avoid fragile wrapping rules

Corporate color is blue (#1A56DB). Use it for CTAs, links, and accent elements only.

---

## 13. Validation Targets

- Must pass long paragraph review（会社概要テーブル、特商法表記）
- Must pass mixed-script heading review（ANIPIA、シリヤト!! の表示）
- Must pass long URL overflow review
- Must pass mobile layout review（ナビ、カード、テーブル）
- Must pass color contrast review（青背景上の白テキスト: WCAG AA準拠）
