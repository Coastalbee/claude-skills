# Slide Templates

Each template shows the HTML pattern, when to use it, and content limits to prevent overflow.

---

## 1. Title Slide

**When:** Opening slide. Sets the topic, author, and mood.

**Limits:** 1 headline (max ~6 words), 1 subtitle line, 1 author line.

```html
<div class="slide slide-title" id="slide-1">
  <div class="slide-num">01 / N</div>
  <div class="top-label animate">
    <!-- Optional: mono label, collab line, category -->
    <span class="label-accent">TOPIC</span>
  </div>
  <h1 class="animate delay-1">Big Bold<br><span class="highlight">Headline</span></h1>
  <p class="subtitle animate delay-2">A serif italic subtitle that adds context</p>
  <div class="divider animate delay-3"></div>
  <p class="author animate delay-3">AUTHOR NAME</p>
</div>
```

**Key CSS:**
- `text-align: center`
- h1: 72px, weight 800, -3px tracking
- subtitle: serif font, italic, 22px, muted color
- Optional `::before` radial glow behind the slide

---

## 2. Quote / Statement Slide

**When:** Bold thesis, provocative claim, or transitional statement. High impact, minimal content.

**Limits:** 1 statement (max ~15 words), 1 optional subtext line.

```html
<div class="slide slide-quote" id="slide-N">
  <div class="slide-num">NN / N</div>
  <p class="big-quote animate">The bold statement goes here with <em>emphasis.</em></p>
  <p class="subtext animate delay-1">Optional supporting context line.</p>
</div>
```

**Key CSS:**
- big-quote: 42px, weight 700, -1.5px tracking, centered, max-width 800px
- `<em>` uses serif font + accent color
- subtext: 18px, muted, max-width 600px

---

## 3. Content Grid Slide (Cards)

**When:** Multiple items with names + descriptions (files, features, tools, concepts).

**Limits:** Max 6 cards (2-column grid). One card can span full width as "primary". Card descriptions max ~20 words each.

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1">Slide Heading</h2>
    <div class="file-grid">
      <div class="file-card primary animate delay-2">
        <div class="file-name">Primary Item</div>
        <div class="file-desc">Description of the most important item.</div>
        <div class="file-badge">LABEL</div>
      </div>
      <div class="file-card animate delay-2">
        <div class="file-name">Item Name</div>
        <div class="file-desc">Short description.</div>
      </div>
      <div class="file-card animate delay-3">
        <div class="file-name">Item Name</div>
        <div class="file-desc">Short description.</div>
      </div>
      <!-- Max 6 cards total -->
    </div>
  </div>
</div>
```

---

## 4. Comparison Slide (Two Columns)

**When:** Before/after, old/new, pros/cons, keep/delegate.

**Limits:** Max 5 items per column. Each item max ~10 words. Optional tags row below.

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1">What changed</h2>
    <div class="comparison">
      <div class="compare-col old animate delay-2">
        <div class="compare-label">❌ The Old Way</div>
        <ul class="compare-list">
          <li>Negative point one</li>
          <li>Negative point two</li>
        </ul>
      </div>
      <div class="compare-col new animate delay-3">
        <div class="compare-label">✓ The New Way</div>
        <ul class="compare-list">
          <li>Positive point one</li>
          <li>Positive point two</li>
        </ul>
      </div>
    </div>
    <!-- Optional: tags row -->
    <div class="tags-row animate delay-4">
      <span class="tag">Tag 1</span>
      <span class="tag">Tag 2</span>
    </div>
  </div>
</div>
```

---

## 5. Tree / Structure Slide

**When:** File systems, folder hierarchies, project structures, org charts.

**Limits:** Max ~15 lines in the tree. Keep comments short (3-4 words).

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content" style="display:flex;flex-direction:column;align-items:center">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1" style="text-align:center">Heading</h2>
    <div class="folder-tree animate delay-2">
      <div><span class="folder">root/</span></div>
      <div class="indent"><span class="highlight">important-file</span> <span class="comment">← note</span></div>
      <div class="indent"><span class="folder">subfolder/</span></div>
      <div class="indent-2">child-item</div>
    </div>
  </div>
</div>
```

---

## 6. Diagram Slide (Multi-Element with Connections)

**When:** Two or more systems/concepts connected by a bridge, flow, or relationship.

**Limits:** 2-3 boxes max. One bridge/connection element. Keep tool tags to 3-4 per box.

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content" style="text-align:center">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1">Heading</h2>
    <div class="machines-diagram animate delay-2">
      <div class="machine-box" style="border-color:var(--secondary)">
        <div class="machine-icon">💻</div>
        <div class="machine-name" style="color:var(--secondary)">Left Thing</div>
        <div class="machine-desc">Short description.</div>
        <div class="machine-tools">
          <span class="machine-tool">Tool 1</span>
          <span class="machine-tool">Tool 2</span>
        </div>
      </div>
      <div class="bridge-arrow">
        <div class="bridge-label">Connection</div>
        <div class="bridge-line"></div>
      </div>
      <div class="machine-box" style="border-color:var(--accent)">
        <div class="machine-icon">🖥️</div>
        <div class="machine-name" style="color:var(--accent)">Right Thing</div>
        <div class="machine-desc">Short description.</div>
        <div class="machine-tools">
          <span class="machine-tool">Tool 1</span>
          <span class="machine-tool">Tool 2</span>
        </div>
      </div>
    </div>
  </div>
</div>
```

---

## 7. Plugin / Feature Cards Slide

**When:** Listing tools, plugins, features, or recommendations with brief descriptions.

**Limits:** Max 4 cards (2×2 grid). Optional full-width warning/callout box at bottom. Descriptions max ~25 words.

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1">Heading</h2>
    <div class="plugin-cards">
      <div class="plugin-card animate delay-2">
        <div class="plugin-name">Feature Name</div>
        <div class="plugin-desc">What it does and why it matters.</div>
      </div>
      <div class="plugin-card animate delay-2">
        <div class="plugin-name">Feature Name</div>
        <div class="plugin-desc">What it does and why it matters.</div>
      </div>
      <!-- Optional warning box -->
      <div class="warning-box animate delay-3">
        <div class="warning-icon">⚠️</div>
        <div class="warning-text"><strong>Important note</strong> with details.</div>
      </div>
    </div>
  </div>
</div>
```

---

## 8. Stats / Results Slide

**When:** Showcasing numbers, metrics, achievements. Big visual impact.

**Limits:** Max 3 stat cards in top row. Max 4 bullet results below. Bullet text max ~15 words each.

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content" style="display:flex;flex-direction:column;align-items:center">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1">Heading</h2>
    <div class="results-grid animate delay-2">
      <div class="result-card">
        <div class="result-emoji">📊</div>
        <div class="result-stat">1,234</div>
        <div class="result-label">What this number means</div>
      </div>
      <div class="result-card">
        <div class="result-emoji">🚀</div>
        <div class="result-stat">99%</div>
        <div class="result-label">Another metric</div>
      </div>
      <div class="result-card">
        <div class="result-emoji">⚡</div>
        <div class="result-stat">5x</div>
        <div class="result-label">Improvement factor</div>
      </div>
    </div>
    <ul class="results-list animate delay-3">
      <li>Key achievement or detail about the results</li>
      <li>Another important outcome</li>
    </ul>
  </div>
</div>
```

---

## 9. Steps / Numbered List Slide

**When:** Sequential instructions, how-to guides, ordered processes.

**Limits:** Max 5 steps. Each step: bold title (3-5 words) + description (max ~20 words).

```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div class="slide-content" style="display:flex;flex-direction:column;align-items:center">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1">Heading</h2>
    <div class="steps-list">
      <div class="step-item animate delay-2">
        <div class="step-num">01</div>
        <div class="step-text"><strong>Step title.</strong> <span>Brief description of what to do.</span></div>
      </div>
      <div class="step-item animate delay-2">
        <div class="step-num">02</div>
        <div class="step-text"><strong>Step title.</strong> <span>Brief description.</span></div>
      </div>
      <div class="step-item animate delay-3">
        <div class="step-num">03</div>
        <div class="step-text"><strong>Step title.</strong> <span>Brief description.</span></div>
      </div>
    </div>
  </div>
</div>
```

---

## 10. Screenshot Showcase Slide

**When:** Showing UI, dashboards, code, or any visual evidence. Screenshots deserve space.

**Limits:** 1 large screenshot OR 2 side-by-side (with captions). Never combine with heavy text content.

### Single Screenshot
```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div style="text-align:center">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1" style="font-size:32px;margin-bottom:24px">What this shows</h2>
    <img class="animate delay-2" src="screenshots/image.png" alt="Description"
         style="width:100%;max-width:1100px;border-radius:12px;border:1px solid var(--border);box-shadow:0 8px 32px rgba(0,0,0,0.5)">
  </div>
</div>
```

### Dual Screenshot
```html
<div class="slide" id="slide-N">
  <div class="slide-num">NN / N</div>
  <div style="text-align:center">
    <div class="section-label animate">SECTION LABEL</div>
    <h2 class="animate delay-1" style="font-size:32px;margin-bottom:24px">Comparison title</h2>
    <div class="animate delay-2" style="display:flex;gap:20px;justify-content:center;flex-wrap:wrap">
      <div>
        <img src="screenshots/left.png" alt="Left" style="width:540px;border-radius:12px;border:1px solid var(--border);box-shadow:0 8px 32px rgba(0,0,0,0.5)">
        <p style="font-size:11px;color:var(--text-dim);margin-top:8px;font-family:'JetBrains Mono',monospace">Caption</p>
      </div>
      <div>
        <img src="screenshots/right.png" alt="Right" style="width:540px;border-radius:12px;border:1px solid var(--border);box-shadow:0 8px 32px rgba(0,0,0,0.5)">
        <p style="font-size:11px;color:var(--text-dim);margin-top:8px;font-family:'JetBrains Mono',monospace">Caption</p>
      </div>
    </div>
  </div>
</div>
```

---

## 11. CTA / Closing Slide

**When:** Final slide. Call to action, links, sign-off.

**Limits:** 1 headline, 1 subtitle, max 2 CTA buttons, 1 author line.

```html
<div class="slide slide-cta" id="slide-N">
  <div class="slide-num">NN / N</div>
  <h2 class="animate delay-1">Call To<br><span class="highlight">Action</span></h2>
  <p class="cta-sub animate delay-2">Serif italic subtitle</p>
  <div class="cta-links animate delay-3">
    <a href="#" class="cta-link primary">Primary Action →</a>
    <a href="#" class="cta-link secondary">Secondary Link</a>
  </div>
  <p class="author-line animate delay-4">AUTHOR NAME</p>
</div>
```

**Key CSS:**
- text-align: center
- h2: 52px, weight 800
- cta-sub: serif italic, 20px, muted
- primary button: accent bg, dark text, hover glow + lift
- secondary button: border only, muted text
