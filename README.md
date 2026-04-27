# Physims – AQA A Level Physics Simulations

Interactive browser-based simulations for AQA A Level Physics, designed for
sixth-form classroom use. Built with plain HTML, CSS and vanilla JavaScript.
Hosted on GitHub Pages.

---

## Live Site

👉 **[millerrd.github.io/physims](https://millerrd.github.io/physims)**

---

## Project Structure

```
physims/
├── index.html              # Homepage – topic cards
├── about.html              # About page
├── sim-template.html       # Reusable simulation page template
├── css/
│   └── style.css           # Custom styles (built on Bulma)
├── topics/
│   ├── year12/             # Year 12 topic pages
│   │   ├── measurements.html
│   │   ├── mechanics.html
│   │   ├── materials.html
│   │   ├── waves.html
│   │   ├── electricity.html
│   │   ├── particles.html
│   │   └── quantum.html
│   └── year13/             # Year 13 topic pages
│       ├── periodic-motion.html
│       ├── gravitational-fields.html
│       ├── electric-fields.html
│       ├── electromagnetism.html
│       ├── nuclear.html
│       ├── capacitance.html
│       └── thermodynamics.html
├── simulations/            # Self-contained JS simulation files
│   └── README.md
└── README.md
```

---

## How to Add a New Simulation

Follow these steps to add a new interactive simulation to Physims.

### 1. Write the simulation JavaScript

Create a self-contained JS file in the `/simulations/` folder, e.g.:

```
simulations/projectile-motion.js
```

The script should export an `init(canvasId, controlsConfig)` function (or
similar) that attaches itself to the canvas element on the page. Keep the
file self-contained — no build step or bundler required.

### 2. Create the simulation HTML page

Copy `sim-template.html` to the appropriate topic folder:

```
topics/year12/projectile-motion.html   # example
```

Edit the copy:
- Update `<title>`, `<meta name="description">` and heading text.
- Replace the placeholder `<div class="sim-placeholder-overlay">` with
  a `<canvas>` element:

  ```html
  <canvas id="simCanvas" width="800" height="500"></canvas>
  ```

- Update the breadcrumb links to point to the correct topic page.
- Customise the sliders, buttons and readout labels in the controls panel.
- At the bottom of `<body>`, load your simulation script:

  ```html
  <script src="../../simulations/projectile-motion.js"></script>
  ```

- Wire up the `simPlay()`, `simPause()` and `simReset()` stubs to your
  simulation's API.

### 3. Link the simulation from the topic page

Open the relevant topic page (e.g. `topics/year12/mechanics.html`) and add
a new simulation card in the `columns is-multiline` section:

```html
<div class="column is-half-tablet is-one-third-desktop">
  <div class="sim-card">
    <div class="sim-card-header">
      <span class="icon"><i class="fa-solid fa-baseball"></i></span>
      <span>Projectile Motion</span>
    </div>
    <div class="sim-card-body">
      <p>Launch a projectile and observe the parabolic path under gravity.</p>
      <a class="button is-small is-light" href="projectile-motion.html">
        <i class="fa-solid fa-play" style="margin-right:.35rem;"></i>Open Simulation
      </a>
    </div>
  </div>
</div>
```

### 4. Test locally

Open `index.html` in your browser (no server needed). Navigate to the topic
page and click the new simulation card. Verify that the simulation loads,
controls work, and the layout looks correct at various viewport widths.

### 5. Submit a pull request

Open a PR with a title such as:

```
feat: add Projectile Motion simulation (Year 12 Mechanics)
```

Include a screenshot of the working simulation in the PR description.

---

## Tech Stack

| Layer | Technology |
|---|---|
| HTML / CSS / JS | Plain (no build step) |
| CSS framework | [Bulma 0.9.4](https://bulma.io) via CDN |
| Icons | [Font Awesome 6.5](https://fontawesome.com) via CDN |
| Hosting | GitHub Pages |

---

## Curriculum Coverage

| Year | Topics |
|---|---|
| Year 12 | Measurements & Errors, Mechanics, Materials, Waves, Electricity, Particles, Quantum |
| Year 13 | Periodic Motion, Gravitational Fields, Electric Fields, Electromagnetism, Nuclear Physics, Capacitance, Thermodynamics |

---

## Licence

[MIT](LICENSE)
