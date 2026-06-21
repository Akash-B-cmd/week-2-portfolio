# Week 2: Styled Portfolio Website

A highly aesthetic, premium, and fully responsive single-page personal portfolio website built with semantic **HTML5** and advanced **CSS3**. It features client-side dual-theme toggling (Light/Dark), custom typography, dynamic glow animations, a sliding mobile hamburger navigation menu, and a responsive multi-column layout utilizing Flexbox and Grid.

---

## 🌟 Key Features

1. **Dual-Theme Custom Property Architecture**: Supported by full dark and light mode variable systems that swap seamlessly with a toggle button.
2. **Highly Interactive UI & Micro-animations**: Focus glow transitions on inputs, scale-and-lift hover states on projects/buttons, and rotating icons.
3. **Fully Responsive Layout**: Flexbox navigation and hero headers, combined with automated CSS Grids that reflow between multi-column desktop grids and stacked single-column mobile views.
4. **Slide-Out Mobile Drawer Menu**: Animated hamburger button ("X" transformation) opening a glassmorphic sidebar menu on screens under `768px`.
5. **Robust Form Validation Styling**: CSS `:valid` and `:invalid` pseudo-class indicators providing instant colored borders and focus glows to input fields.

---

## 📂 Project Structure

```text
Week 2 Portfolio/
│
├── index.html            # Main HTML document with custom sections & interactive JS
├── style.css             # Unified CSS design system (variables, layouts, media queries)
├── README.md             # Project documentation (Week 2 Submission guide)
│
├── images/               # Media asset library
│   ├── profile.png       # Professional developer avatar
│   ├── project1.png      # Agency Landing Page project screenshot
│   ├── project2.png      # Analytics Dashboard mockup
│   └── project3.png      # Mobile E-commerce UI mockup
│
└── screenshots/          # Proof-of-work documentation screenshots
    ├── desktop-dark.png  # Desktop layout (default Dark theme)
    ├── desktop-light.png # Desktop layout (Light theme toggled)
    ├── mobile-nav-open.png # Mobile drawer navigation open
    ├── mobile-light.png  # Mobile layout in Light theme
    └── form-submission.png # Contact form success notification
```

---

## 🚀 Setup & Local Execution Instructions

To launch the portfolio website locally:

1. **Clone/Download** the repository folder to your local computer.
2. **Launch in Browser**:
   - Double-click the [index.html](file:///c:/Users/24r11/OneDrive/Documents/Week%201%20(wt)/index.html) file to open it in Chrome, Firefox, Edge, or Safari.
   - Alternatively, drag-and-drop the file into a browser tab.
3. **Developer Environment (Recommended)**:
   - Open the directory in **VS Code**.
   - Install the **Live Server** extension.
   - Right-click `index.html` and select **Open with Live Server** to view hot-reloads of changes.

---

## 🛠️ Technical Details & CSS Architecture

### 1. The Cascade, Specificity, and Selector Strategy
CSS rules are executed based on the rules of the **Cascade** (Importance, Source Order, and Specificity). This project makes structured use of specific selector combinations to style targets without adding code bloat:

- **Element Selectors** (Low Specificity): `html`, `body`, `header`, `nav`, `section`, `a`. Used for resetting defaults (e.g., margin/padding) and specifying global typography fonts and line-heights.
- **Class Selectors** (Medium Specificity): `.logo`, `.btn`, `.about-card`, `.skills-category`, `.form-control`. Used for reusable layout cells, utility designs, buttons, and individual cards.
- **ID Selectors** (High Specificity): `#hero`, `#about`, `#skills`, `#contact`, `#theme-toggle`. Target specific, unique single-instance sections for anchor scrolling and JS hooks.
- **Pseudo-classes & Pseudo-elements**:
  - Hover & Focus states: `:hover`, `:focus` (adds transition scaling, shadow glows, and border color adjustments).
  - Child indices: `:nth-child(n)`, `:last-child` (used for selecting lines of the hamburger bar or spacing elements).
  - Validation: `:valid`, `:invalid` (used for coloring input focus borders dynamically).
  - Pseudo-elements: `::before` and `::after` (create background ambient blur circles, line underscores under header links, and overlay screens).
- **Attribute Selectors**: `[data-theme="light"]` targets the document's root tag when light mode is enabled, cleanly overriding CSS properties.

### 2. Layout Strategies (Grid & Flexbox)
Modern layout models ensure visual alignment without hardcoded positions:
- **CSS Flexbox**:
  - Header Nav (`.header-container` and `.header-right`): Aligns elements along the horizontal axis, keeping logo and links spaced on extremes (`justify-content: space-between`) and centered vertically (`align-items: center`).
  - Hero Section (`.hero-container`): Flexbox aligns the text description and avatar image side-by-side on desktop, then reverses order vertically on mobile (`flex-direction: column-reverse`) so text is readable above the fold.
- **CSS Grid**:
  - About Grid (`.about-grid`): Uses a asymmetric layout (`grid-template-columns: 1.5fr 1fr`) to distribute information (biography card on the left, statistics stacks on the right).
  - Projects and Skills lists (`.projects-gallery` and `.skills-container`): Fulfill responsiveness automatically using `grid-template-columns: repeat(auto-fit, minmax(300px, 1fr))`. This instructs the browser to fit as many cards of at least `300px` as possible, wrapping them to subsequent rows automatically as screen width shrinks.

### 3. CSS Variables & Theme Management
Color schemes are separated into custom variables in the `:root` scope, allowing instant site-wide theme switching by overriding variables in the `[data-theme="light"]` selector:

| Variable | Dark Theme (Default) | Light Theme | Role |
| :--- | :--- | :--- | :--- |
| `--bg-main` | `#0b0f17` (Deep blue-black) | `#f8fafc` (Soft slate white) | Main background |
| `--bg-card` | `rgba(20, 28, 47, 0.6)` | `rgba(255, 255, 255, 0.7)` | Backdrop cards |
| `--text-primary` | `#f8fafc` (Off-white) | `#0f172a` (Slate 900) | Primary headers and body text |
| `--text-secondary` | `#94a3b8` (Slate 400) | `#475569` (Slate 600) | Description paragraphs |
| `--border-color` | `rgba(255, 255, 255, 0.08)` | `rgba(15, 23, 42, 0.08)` | Silent boundaries |
| `--color-primary` | `#6366f1` (Indigo 500) | `#4f46e5` (Indigo 600) | Major accents & gradient start |
| `--color-secondary`| `#06b6d4` (Cyan 500) | `#0891b2` (Cyan 600) | Accent highlights & gradient end |

---

## 📱 Responsiveness Strategy & Mobile Adaptability

Responsiveness is implemented via cascading **CSS Media Queries** combined with relative layout units:

- **Viewport Tag**: `<meta name="viewport" content="width=device-width, initial-scale=1.0">` is defined in the `<head>` of [index.html](file:///c:/Users/24r11/OneDrive/Documents/Week%201%20(wt)/index.html), instructing mobile browsers to render elements on a 1:1 pixel scale.
- **Responsive Navigation Drawer (`@media (max-width: 768px)`)**:
  - The standard desktop header link list is hidden.
  - The hamburger icon button (`.hamburger-btn`) appears in the header.
  - The `<nav>` menu transforms into a fixed vertical sidebar (`position: fixed`, `width: 280px`, `right: -100%`) positioned below the header.
  - Toggling the `.active` class slides the drawer into view (`right: 0`) and animates the three hamburger bars into an "X" shape through CSS transforms (`rotate` and `translate`).
  - To preserve layout integrity, on screens smaller than `600px`, the drawer's `top` margin adjusts to `60px` to match the reduced height of the mobile sticky header.
- **Fluid Layout Reflows**:
  - At widths `<= 900px`, flex items and grids break into vertical stacks, wrapping content within the mobile viewport.
  - Interactive buttons and text sizes scale automatically using relative `rem` units, which scale based on the root font size (which scales down to `14px` on screen widths `<= 600px`).

---

## 📸 Visual Documentation (Screenshots)

The screenshots below demonstrate the styling and responsive behaviors in both themes and views:

### 1. Desktop Layout (Dark & Light Themes)
| Dark Mode (Default) | Light Mode (Toggled) |
| :---: | :---: |
| ![Desktop Dark Theme](screenshots/desktop-dark.png) | ![Desktop Light Theme](screenshots/desktop-light.png) |

### 2. Mobile Layout & Responsive Navigation Menu
| Mobile View (Light Theme) | Sliding Mobile Nav Open (Dark Theme) |
| :---: | :---: |
| ![Mobile Light Layout](screenshots/mobile-light.png) | ![Mobile Drawer Navigation](screenshots/mobile-nav-open.png) |

### 3. Interactive Elements (Form Submission State)
| Contact Form State |
| :---: |
| ![Form Validation & Submission Success](screenshots/form-submission.png) |

---

## 🧪 Testing Evidence & Validation

Interactive functionality and responsive rendering have been rigorously validated across multiple test cases:

### Manual Test Cases & Results

1. **Theme Switching**
   - *Action*: Click the floating sun/moon icon button in the header.
   - *Result*: Document `data-theme` attribute switches between `'dark'` and `'light'` immediately. Background elements transition smoothly over `0.3s`. Variables update instantly. Preference is stored in browser local storage and loaded automatically on page refresh.

2. **Mobile Hamburger Menu Slide-out**
   - *Action*: Resize browser window below `768px`. Click the hamburger button.
   - *Result*: The hamburger button lines cross into an "X". The menu drawer slides in from the right. The background outside the drawer continues to show a slight blur, and scrolling is constrained.
   - *Action*: Click a menu navigation link (e.g. "Skills").
   - *Result*: The website scrolls smoothly to the `#skills` section, and the mobile menu closes automatically.
   - *Action*: Click anywhere outside the menu drawer.
   - *Result*: The menu drawer closes, and the hamburger button resets.

3. **Contact Form Validation & Focus Indicators**
   - *Action*: Click on the Name field and leave it blank.
   - *Result*: When focus is lost, no indicator shows. When focused, if input is invalid, the border glows red (`#ef4444`).
   - *Action*: Enter a single character in the message field.
   - *Result*: The field remains invalid because the `minlength` is set to `10`. The border glows red on focus.
   - *Action*: Enter valid email, name, and message details and click "Send Message".
   - *Result*: The input borders glow cyan on focus. Clicking the button simulates transmission, showing "Sending your message...", followed by a green success message: "Thank you, [Name]! Your message was successfully sent.", and clears the input fields.
