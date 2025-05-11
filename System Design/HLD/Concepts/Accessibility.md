# Accessibility

A screen reader interprets the HTML structure and ARIA (Accessible Rich Internet Applications) attributes to determine what is on the screen.

# 📘 Accessibility in Frontend: ARIA Attributes Cheat Sheet

ARIA (Accessible Rich Internet Applications) attributes help enhance accessibility, especially for screen reader users. Below is a list of commonly used ARIA attributes and their use cases.

---

### 🔹 1. `aria-label`

**Purpose:** Provides a custom, accessible label for an element.

**When to use:** When there’s no visible text label but you still want to describe the element for screen readers.

```html
<button aria-label="Close modal">✖</button>
```

---

### 🔹 2. `aria-labelledby`

**Purpose:** Associates the element with another element’s text label via ID reference.

**When to use:** When the label already exists in the DOM.

```html
<h2 id="section-title">Settings</h2>
<div aria-labelledby="section-title">...</div>
```

---

### 🔹 3. `aria-describedby`

**Purpose:** Associates additional descriptive text with an element.

**When to use:** For tooltips, form hints, or error messages.

```html
<input type="text" aria-describedby="email-hint" />
<span id="email-hint">Enter a valid email address.</span>
```

---

### 🔹 4. `aria-hidden`

**Purpose:** Hides elements from screen readers.

**When to use:** For purely decorative content or when duplicate content should be ignored.

```html
<div aria-hidden="true">👋 Decorative Emoji</div>
```

---

### 🔹 5. `aria-live`

**Purpose:** Announces updates in dynamic content areas.

**When to use:** For live regions like notifications, status messages, or live updates.

**Values:** `polite`, `assertive`, `off`

```html
<div aria-live="polite">You have new notifications.</div>
```

---

### 🔹 6. State Attributes (`aria-checked`, `aria-selected`, `aria-expanded`, `aria-pressed`)

**Purpose:** Describe the current state of interactive UI elements.

**When to use:** For custom widgets or interactive elements without native state indicators.

```html
<!-- Toggle button -->
<button aria-pressed="true">Bold</button>

<!-- Accordion -->
<button aria-expanded="false">Show More</button>
```

---

### 🔹 7. `role`

**Purpose:** Defines the semantic role of an element.

**When to use:** When native HTML semantics are not used, especially for custom components.

```html
<div role="dialog" aria-labelledby="dialog-title">
  <h2 id="dialog-title">Confirm Delete</h2>
</div>
```

---

### 🔹 8. `role="alert"`

**Purpose:** Announces an element immediately when it appears.

**When to use:** For urgent messages like form errors or critical alerts.

```html
<div role="alert">There was an error processing your request.</div>
```

---
