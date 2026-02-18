# Cohorts Week 1: Frontend Basics (Portfolio)

Build your first portfolio page with HTML and CSS!

```
git clone git@github.com:CSES-Open-Source/cohorts-wi26-week1-frontend.git
```

---

# PREREQUISITES

Make sure you have **VS Code** installed:
- Download from [https://code.visualstudio.com](https://code.visualstudio.com)
- Install the **Live Server** extension for easy previewing

---

# SETUP

### TODO 1: Create Your Project Folder

Create a new folder with your name under the root directory:

```bash
mkdir your-name
```

### TODO 2: Copy the Template Files

```bash
cp -r template/* your-name/
cd your-name
```

You should now have:
```
your-name/
├── index.html
└── style.css
```

Open `index.html` with Live Server to see your progress as you build!

---

# SECTION 1: HTML Boilerplate

> **NEW CONCEPTS:** Document structure, meta tags, linking stylesheets

Every HTML file starts with this structure:

### TODO 3: Add the HTML Boilerplate

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Name | Portfolio</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

</body>
</html>
```

**What each part does:**
| Tag | Purpose |
|-----|---------|
| `<!DOCTYPE html>` | Tells the browser this is HTML5 |
| `<html lang="en">` | Root element, sets language to English |
| `<head>` | Metadata (not visible on page) |
| `<meta charset="UTF-8">` | Supports special characters |
| `<meta name="viewport">` | Makes it work on mobile |
| `<title>` | Text shown in browser tab |
| `<link rel="stylesheet">` | Connects your CSS file |
| `<body>` | All visible content goes here |

---

# SECTION 2: Base Styles + CSS Variables

> **NEW CONCEPTS:** Universal selector (`*`), box-sizing, `:root`, CSS custom properties, `var()`

Before building sections, let's set up our foundation.

---

## Quick Reference: px vs rem vs em

| Unit | What It Means | When To Use |
|------|---------------|-------------|
| `px` | Fixed pixels — never changes | Borders, shadows, max-width, fixed widths |
| `rem` | Relative to **root** font size (usually 16px) | Fonts, padding, margins, gap |
| `em` | Relative to **parent** font size | Rarely — can get confusing with nesting |

**Simple rule:** Use `rem` for spacing and fonts, `px` for layout constraints and details.

**Examples:**
```css
/* rem - for spacing and fonts */
padding: 2rem;        /* 2 × 16px = 32px */
font-size: 1.25rem;   /* 1.25 × 16px = 20px */
margin: 1rem auto;

/* px - for layout constraints and details */
max-width: 800px;     /* screen-based constraint */
width: 300px;         /* fixed card size */
border: 1px solid black;
box-shadow: 0 2px 4px rgba(0,0,0,0.1);
```

**Why rem for spacing/fonts?**
- More accessible — users who set larger browser font sizes see text and spacing scale
- Easier to maintain — change the root font size, everything adjusts

**Why px for widths?**
- Layout constraints are about screen real estate, not font size
- `max-width: 800px` means "fit this many pixels on screen" regardless of text size

---

### TODO 4: Add Base Reset

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

**What this does:**
- `*` → Selects ALL elements (universal selector)
- `margin: 0; padding: 0;` → Removes default browser spacing
- `box-sizing: border-box;` → Makes width/height include padding and border

### TODO 5: Add CSS Variables

```css
:root {
    --color-primary: #2c3e50;
    --color-accent: #3498db;
    --color-light: #f8f9fa;
    --color-text: #333;
    --color-text-light: #bdc3c7;
}
```

**What this does:**
- `:root` → Targets the root element (highest level, applies everywhere)
- `--color-primary` → Creates a reusable variable
- Later, use `var(--color-primary)` to reference it

**Why variables?**
- Change one value → updates everywhere
- Makes color relationships explicit
- Sets up for dark mode later (JavaScript week!)

### TODO 6: Add Body Styles

```css
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: var(--color-text);
}
```

---

# SECTION 3: Hero Section

> **NEW CONCEPTS:** `<header>` tag, class attribute, class selector, `padding`, `text-align`, descendant selector

The hero is the first thing visitors see — your name and title.

### TODO 7: Hero HTML

```html
<header class="hero">
    <h1>Your Name</h1>
    <p class="subtitle">Aspiring Software Engineer</p>
</header>
```

**Where:** Inside `<body>`

**New tags:**
| Tag | Purpose |
|-----|---------|
| `<header>` | Semantic tag for introductory content |
| `<h1>` | Main heading (use only once per page) |
| `class="hero"` | Name for CSS to target |

### TODO 8: Hero CSS

```css
.hero {
    background-color: var(--color-primary);
    color: white;
    text-align: center;
    padding: 4rem 2rem;
}

.hero h1 {
    font-size: 2.5rem;
    margin-bottom: 0.5rem;
}

.subtitle {
    font-size: 1.25rem;
    color: var(--color-text-light);
}
```

**New concepts:**
| Syntax | What it does |
|--------|--------------|
| `.hero` | Class selector — targets elements with `class="hero"` |
| `.hero h1` | Descendant selector — targets `<h1>` inside `.hero` |
| `padding: 4rem 2rem` | 4rem top/bottom, 2rem left/right |
| `var(--color-primary)` | Uses the CSS variable we defined |

**Check your browser!** You should see a dark blue header with your name.

---

# SECTION 4: About Section

> **NEW CONCEPTS:** `<main>`, `<section>`, `max-width`, `margin: auto` for centering

### TODO 9: About HTML

```html
<main>
    <section class="about">
        <h2>About Me</h2>
        <p>
            Hi! I'm a student at UC San Diego studying Computer Science.
            I love building things for the web and learning new technologies.
        </p>
    </section>
</main>
```

**Where:** After `</header>`, inside `<body>`

**New tags:**
| Tag | Purpose |
|-----|---------|
| `<main>` | Semantic tag for primary page content |
| `<section>` | Groups related content |
| `<h2>` | Subheading (smaller than h1) |

### TODO 10: About CSS

```css
.about {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 2rem;
}

.about h2 {
    margin-bottom: 1rem;
}
```

**New concepts:**
| Property | What it does |
|----------|--------------|
| `max-width: 800px` | Content won't grow wider than 800px |
| `margin: 2rem auto` | 2rem top/bottom, `auto` centers horizontally |

**Check your browser!** The about section should be centered with readable width.

---

# SECTION 5: Projects Section

> **NEW CONCEPTS:** `<div>` for grouping, `<a>` links, Flexbox (`display: flex`, `justify-content`, `gap`), `border-radius`, `box-shadow`

This section introduces **Flexbox** — the modern way to create layouts.

### TODO 11: Projects HTML

```html
<section class="projects">
    <h2>Projects</h2>
    <div class="project-grid">
        <div class="project-card">
            <h3>Project One</h3>
            <p>A short description of what this project does and the technologies used.</p>
            <a href="https://github.com/yourusername/project">View on GitHub</a>
        </div>
        <div class="project-card">
            <h3>Project Two</h3>
            <p>Another project with a brief description of its features.</p>
            <a href="https://github.com/yourusername/project">View on GitHub</a>
        </div>
    </div>
</section>
```

**Where:** Inside `<main>`, after the about section

**New tags:**
| Tag | Purpose |
|-----|---------|
| `<div>` | Generic container for grouping elements |
| `<h3>` | Smaller heading for card titles |
| `<a href="...">` | Link to another page |

### TODO 12: Projects Container CSS

```css
.projects {
    background-color: var(--color-light);
    padding: 3rem 2rem;
}

.projects h2 {
    text-align: center;
    margin-bottom: 2rem;
}

.project-grid {
    display: flex;
    justify-content: center;
    gap: 2rem;
    max-width: 900px;
    margin: 0 auto;
}
```

**Flexbox explained:**
| Property | What it does |
|----------|--------------|
| `display: flex` | Arranges children in a row (by default) |
| `justify-content: center` | Centers items horizontally |
| `gap: 2rem` | Adds space between flex items |

### TODO 13: Project Card CSS

```css
.project-card {
    background: white;
    padding: 1.5rem;
    border-radius: 8px;
    width: 300px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.project-card h3 {
    margin-bottom: 0.5rem;
    color: var(--color-primary);
}

.project-card p {
    margin-bottom: 1rem;
    color: #666;
}

.project-card a {
    color: var(--color-accent);
    text-decoration: none;
}
```

**New concepts:**
| Property | What it does |
|----------|--------------|
| `border-radius: 8px` | Rounds the corners |
| `box-shadow: 0 2px 4px rgba(0,0,0,0.1)` | Adds a subtle shadow |
| `text-decoration: none` | Removes underline from links |

**Box-shadow breakdown:** `horizontal vertical blur color`
- `0` = no horizontal offset
- `2px` = 2px down
- `4px` = blur radius
- `rgba(0,0,0,0.1)` = black at 10% opacity

**Check your browser!** You should see two cards side by side.

---

# SECTION 6: Footer

> **NEW CONCEPTS:** `<footer>`, `<ul>`/`<li>` lists, `mailto:` links, `list-style: none`

### TODO 14: Footer HTML

```html
<footer class="footer">
    <p>Connect with me:</p>
    <ul class="social-links">
        <li><a href="https://github.com/yourusername">GitHub</a></li>
        <li><a href="https://linkedin.com/in/yourusername">LinkedIn</a></li>
        <li><a href="mailto:your@email.com">Email</a></li>
    </ul>
</footer>
```

**Where:** After `</main>`, before `</body>`

**New tags:**
| Tag | Purpose |
|-----|---------|
| `<footer>` | Semantic tag for page footer |
| `<ul>` | Unordered list |
| `<li>` | List item |
| `mailto:` | Opens user's email client |

### TODO 15: Footer CSS

```css
.footer {
    background-color: var(--color-primary);
    color: white;
    text-align: center;
    padding: 2rem;
}

.social-links {
    list-style: none;
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin-top: 1rem;
}

.social-links a {
    color: var(--color-accent);
    text-decoration: none;
}
```

**New concept:**
- `list-style: none` → Removes the bullet points from the list

**Check your browser!** Footer should match the hero with horizontal links.

---

# BONUS: Hover Effects

> **NEW CONCEPTS:** `:hover` pseudo-class, `transform`, `transition`

Make your portfolio feel interactive!

### BONUS TODO 1: Add Smooth Transitions

Add this to your existing `.project-card` rule:

```css
.project-card {
    /* ...existing styles... */
    transition: transform 0.2s, box-shadow 0.2s;
}
```

### BONUS TODO 2: Add Hover States

```css
.project-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

.social-links a:hover {
    color: #5dade2;
}

.project-card a:hover {
    text-decoration: underline;
}
```

**New concepts:**
| Syntax | What it does |
|--------|--------------|
| `:hover` | Applies styles when mouse is over element |
| `transform: translateY(-4px)` | Moves element up 4 pixels |
| `transition` | Animates the change smoothly |

---

# BONUS: Profile Image

> **NEW CONCEPTS:** `<img>` tag, `border-radius: 50%`, `object-fit`

### BONUS TODO 3: Add Image to Hero HTML

Update your hero section:

```html
<header class="hero">
    <img src="profile.jpg" alt="Your Name" class="profile-img">
    <h1>Your Name</h1>
    <p class="subtitle">Aspiring Software Engineer</p>
</header>
```

**New tag:**
| Attribute | Purpose |
|-----------|---------|
| `src` | Path to the image file |
| `alt` | Description for accessibility (screen readers) |

### BONUS TODO 4: Profile Image CSS

```css
.profile-img {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 1rem;
    border: 3px solid white;
}
```

**New concepts:**
| Property | What it does |
|----------|--------------|
| `border-radius: 50%` | Makes a perfect circle |
| `object-fit: cover` | Image fills space without distortion |

---

# CONGRATS!

You've built your first portfolio page with HTML and CSS!

## What You Learned

| Concept | Where You Used It |
|---------|-------------------|
| HTML document structure | Boilerplate |
| CSS variables (`:root`) | Color theming |
| Semantic tags | header, main, section, footer |
| Class selectors | .hero, .about, .projects |
| Flexbox layout | Project grid, social links |
| Box model | Padding, margin, borders |
| Hover effects | Cards, links |

## Next Week

We'll add **JavaScript** to make your portfolio interactive!
