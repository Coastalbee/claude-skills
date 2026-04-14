# Design System Reference

> This is a **reference** extracted from a proven presentation. Use it as inspiration — create fresh palettes and typography for each new presentation. Don't copy blindly.

## CSS Custom Properties

```css
:root {
  /* Backgrounds */
  --bg: #08080a;
  --surface: #111114;
  --surface-2: #19191d;
  --border: #25252b;

  /* Text */
  --text: #f5f5f7;
  --text-muted: #9898a0;
  --text-dim: #606068;

  /* Accent colors — change per presentation */
  --accent: #FF4D4D;
  --accent-glow: rgba(255, 77, 77, 0.12);

  /* Supporting colors (optional, topic-specific) */
  --secondary: #6c31e3;
  --secondary-glow: rgba(108, 49, 227, 0.12);
  --tertiary: #CC7B4A;
  --tertiary-glow: rgba(204, 123, 74, 0.12);
  --green: #22c55e;
  --blue: #4285f4;
}
```

### Color Strategy
- Dark background (#08-#11 range) with light text
- Accent color for highlights, active states, primary borders, numbers
- Glow variants (12% opacity) for subtle background radials and box shadows
- Supporting colors for secondary elements (comparison columns, brand-specific items)
- `--green` for positive/new states, dimmed styles for negative/old states

## Typography

### Font Pairing
```html
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;500;600;700;800&family=Newsreader:ital,wght@0,400;0,600;1,400&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
```

| Role | Font | Usage |
|------|------|-------|
| Display / Headings | **Sora** (800, 700, 600) | h1, h2, slide titles, big numbers |
| Serif accent | **Newsreader** (italic) | Subtitles, quotes, editorial flourish |
| Mono / Labels | **JetBrains Mono** | Counters, section labels, badges, file names, code |

### Scale
| Element | Size | Weight | Tracking |
|---------|------|--------|----------|
| Hero h1 | 72px | 800 | -3px |
| Slide h2 | 44px | 700 | -1.5px |
| CTA h2 | 52px | 800 | -2px |
| Big quote | 42px | 700 | -1.5px |
| Screenshot title | 32px | 700 | — |
| Subtitle (serif) | 22px | 400 italic | — |
| Body text | 16px | 400 | — |
| Card description | 14px | 400 | — |
| Section label | 12px | 400 | 3px uppercase |
| Slide counter | 12px | 400 | 1px |
| Badge / tag | 10-12px | 400-500 | 1-2px |

## Base Styles

```css
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; scroll-snap-type: y mandatory; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: 'Sora', sans-serif;
  overflow-x: hidden;
}
```

## Slide Container

```css
.slide {
  min-height: 100vh;
  scroll-snap-align: start;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 60px 80px;
  position: relative;
  overflow: hidden;
}
```

## Slide Counter

```css
.slide-num {
  position: absolute;
  top: 32px;
  right: 40px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  color: var(--text-dim);
  letter-spacing: 1px;
}
```

## Navigation Dots

```css
.nav-dots {
  position: fixed;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 12px;
  z-index: 100;
}
.nav-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--text-dim);
  opacity: 0.3;
  cursor: pointer;
  transition: all 0.3s;
}
.nav-dot.active {
  opacity: 1;
  background: var(--accent);
  box-shadow: 0 0 8px var(--accent-glow);
}
```

## Component Styles

### Section Label
```css
.section-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 12px;
}
```

### Cards (Content Grid)
```css
.file-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
.file-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 24px;
  transition: border-color 0.2s;
}
.file-card:hover { border-color: #3a3a42; }
.file-card.primary {
  grid-column: 1 / -1;
  border-color: var(--accent);
  background: linear-gradient(135deg, var(--accent-glow), transparent);
}
```

### Comparison Columns
```css
.comparison {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}
.compare-col {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 28px;
}
.compare-col.old { opacity: 0.5; border-style: dashed; }
.compare-col.new {
  border-color: var(--green);
  background: linear-gradient(135deg, rgba(34, 197, 94, 0.04), transparent);
}
```

### Folder Tree
```css
.folder-tree {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 32px 40px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 14px;
  line-height: 2;
  color: var(--text-muted);
  max-width: 700px;
}
.folder-tree .folder { color: var(--text); font-weight: 600; }
.folder-tree .highlight { color: var(--accent); }
.folder-tree .comment { color: var(--text-dim); font-size: 12px; }
.folder-tree .indent { padding-left: 24px; }
.folder-tree .indent-2 { padding-left: 48px; }
```

### Machine Diagram
```css
.machines-diagram {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 40px;
}
.machine-box {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 36px 40px;
  width: 320px;
  text-align: center;
}
/* Add colored border + glow per box */
```

### Plugin/Feature Cards
```css
.plugin-cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
.plugin-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 28px;
}
```

### Stats/Results
```css
.results-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.result-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 24px;
  text-align: center;
}
.result-stat {
  font-family: 'JetBrains Mono', monospace;
  font-size: 28px;
  font-weight: 700;
  color: var(--accent);
}
```

### Steps List
```css
.steps-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 700px;
}
.step-item {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  padding: 20px 24px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
}
.step-num {
  font-family: 'JetBrains Mono', monospace;
  font-size: 24px;
  font-weight: 700;
  color: var(--accent);
  flex-shrink: 0;
  width: 40px;
}
```

### CTA Buttons
```css
.cta-link {
  font-family: 'JetBrains Mono', monospace;
  font-size: 14px;
  padding: 14px 28px;
  border-radius: 8px;
  text-decoration: none;
  transition: all 0.2s;
}
.cta-link.primary {
  background: var(--accent);
  color: #000;
  font-weight: 600;
}
.cta-link.primary:hover {
  box-shadow: 0 0 30px var(--accent-glow);
  transform: translateY(-2px);
}
.cta-link.secondary {
  border: 1px solid var(--border);
  color: var(--text-muted);
}
```

### Tags/Badges
```css
.badge {
  display: inline-block;
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  letter-spacing: 1px;
  padding: 3px 8px;
  border-radius: 4px;
  background: var(--accent-glow);
  color: var(--accent);
}
.tag {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  padding: 6px 14px;
  border-radius: 6px;
  background: var(--surface-2);
  border: 1px solid var(--border);
  color: var(--text-muted);
}
```

### Warning/Callout Box
```css
.warning-box {
  grid-column: 1 / -1;
  background: linear-gradient(135deg, var(--secondary-glow), transparent);
  border: 1px solid var(--secondary);
  border-radius: 12px;
  padding: 24px 28px;
  display: flex;
  align-items: flex-start;
  gap: 16px;
}
```

## Animation System

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
.animate { opacity: 0; }
.animate.visible { animation: fadeUp 0.6s ease forwards; }
.delay-1 { animation-delay: 0.1s; }
.delay-2 { animation-delay: 0.2s; }
.delay-3 { animation-delay: 0.3s; }
.delay-4 { animation-delay: 0.4s; }
```

### Glow Effect (behind title slides)
```css
.slide-title::before {
  content: '';
  position: absolute;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, var(--accent-glow) 0%, transparent 70%);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
}
```
