# SVG.js — Lightweight JSON-Driven SVG Icon Engine

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

> A zero-dependency, JSON-driven SVG icon rendering engine for the modern Indonesian web ecosystem.

---

## Overview

**SVG.js** is a lightweight client-side rendering engine that maps icon keys to inline SVG paths through a simple JSON dictionary. It eliminates external font dependencies, reduces HTTP overhead, and enables full CSS customization through custom properties — designed specifically for low-bandwidth, resource-constrained educational web environments.

This library is part of the **DonatJS ecosystem**:

```
donat (structure) → wafel (appearance) → cenil (visual language) → piawai (learning)
```

SVG.js serves as the visual language layer (`cenil`), providing a curated icon vocabulary for web applications built on the DonatJS JSON-driven MVC framework.

---

## Features

- **Zero dependency** — pure vanilla JavaScript, no npm, no bundler
- **JSON-driven** — icon paths stored as a flat key-value dictionary in `svg.path`
- **Inline SVG injection** — icons rendered directly into the DOM, fully styleable via CSS
- **DonatJS pattern** — `<i class="di-{key}"></i>` markup convention
- **CSS custom property theming** — colors controlled via `--pColor`, `--sColor`, `--aColor`
- **Interactive gallery** — built-in icon browser with search, multi-zoom, and clipboard copy
- **60+ icons** — UI primitives, social brands, and ecosystem identity icons

---

## Quick Start

### 1. Include the files

```html
<link rel="stylesheet" href="svg.css">
<script src="svg.js"></script>
```

### 2. Use an icon

```html
<i class="di-donat"></i>
<i class="di-search"></i>
<i class="di-instagram"></i>
```

### 3. Initialize rendering

```html
<script>
  if (typeof svg !== 'undefined') svg.di();
</script>
```

---

## API Reference

### `svg.path`

A flat JSON object mapping icon keys to SVG path `d` attribute strings.

```js
svg.path.donat  // → "M12 10C7 5 4 14 12 17..."
svg.path.search // → "M20 11A1 1 0 002 11..."
```

### `svg.icon(id)`

Returns a complete `<svg>` element string for the given icon key.

```js
var html = svg.icon('donat');
// → '<svg class="svgicon" xmlns="..." viewBox="0 0 24 24"><path d="..."/></svg>'
```

| Parameter | Type   | Default   | Description          |
|-----------|--------|-----------|----------------------|
| `id`      | string | `'bayam'` | Icon key from `svg.path` |

### `svg.di()`

Scans the DOM for all elements matching `.di-{key}` class names and injects the corresponding SVG icon via `innerHTML`. Call after DOM is ready, and again after any dynamic content insertion.

```js
svg.di(); // inject all icons found in current DOM
```

---

## Icon Reference

### UI & Navigation

| Key         | Description            |
|-------------|------------------------|
| `menu`      | Hamburger menu         |
| `search`    | Search / magnifier     |
| `filter`    | Slider filter          |
| `threedots` | Vertical ellipsis      |
| `house`     | Home                   |
| `person`    | User / profile         |
| `eye`       | View / visibility      |
| `geo`       | Location pin           |
| `scan`      | QR / barcode scan      |
| `setting`   | Settings / gear        |
| `lock`      | Lock / security        |
| `bel`       | Notification bell      |
| `calendar`  | Date picker            |

### Actions

| Key        | Description        |
|------------|--------------------|
| `upload`   | Upload             |
| `download` | Download           |
| `save`     | Save / floppy disk |
| `pen`      | Edit / write       |
| `trush`    | Delete / trash     |
| `check`    | Checkmark          |
| `plus`     | Add / plus circle  |
| `minus`    | Remove / minus     |
| `undo`     | Undo               |
| `redo`     | Redo               |
| `printer`  | Print              |
| `camera`   | Camera / photo     |
| `link`     | Hyperlink          |
| `copy`     | Copy               |

### Content & Data

| Key        | Description         |
|------------|---------------------|
| `file`     | Generic file        |
| `buku`     | Book                |
| `edu`      | Education / mortarboard |
| `chart`    | Line chart          |
| `card`     | Credit / ID card    |
| `cart`     | Shopping cart       |
| `envelope` | Email               |
| `qrcode`   | QR code             |
| `code`     | Code / developer    |
| `web`      | Globe / website     |

### Social & Brand

| Key         | Description  |
|-------------|--------------|
| `twitter`   | Twitter / X  |
| `x`         | X logo       |
| `facebook`  | Facebook     |
| `instagram` | Instagram    |
| `whatsapp`  | WhatsApp     |
| `linkedin`  | LinkedIn     |
| `youtube`   | YouTube      |
| `github`    | GitHub       |
| `discord`   | Discord      |
| `arduino`   | Arduino      |
| `credly`    | Credly       |
| `orcid`     | ORCID        |

### Ecosystem Identity

| Key       | Description                        |
|-----------|------------------------------------|
| `donat`   | DonatJS framework logo             |
| `bayam`   | BayamJS framework logo             |
| `ktupad`  | Ktupad platform logo               |
| `piawai`  | Piawai learning platform logo      |
| `sismadi` | Sismadi / PT Sismadi Langit Solusi |
| `sls`     | SLS brand mark                     |
| `ws`      | WS identifier                      |

---

## Theming

Override CSS custom properties to match your brand:

```css
:root {
  --pColor: #00738e;  /* primary — icon stroke color */
  --sColor: #00738e;  /* secondary — hover state */
  --aColor: #DF8C43;  /* accent — interactive highlight */
}
```

Icons inherit `stroke` from `--pColor` by default. Hover state transitions to `--aColor` with a dash-animation effect.

---

## Gallery

Open `index.html` in a browser to explore all available icons. The gallery supports:

- **Search** — filter by icon name
- **THUMB** — default grid view
- **LIST** — compact list with path preview
- **1×** — small grid
- **2×** — large zoom grid
- **Click to copy** — click any icon to copy `<i class="di-{key}"></i>` to clipboard

---

## Adding Icons

Add a new entry to `svg.path` in `svg.js`:

```js
var svg = {
  path: {
    // existing icons...
    myicon: `M12 2 L22 22 L2 22 Z`,
  }
};
```

All paths use a `24×24` viewBox coordinate space. The key becomes the class name: `di-myicon`.

---

## File Structure

```
svg/
├── svg.js        # Core engine — path dictionary + API
├── svg.css       # Base styles + CSS custom properties
├── index.html    # Interactive icon gallery
├── README.md     # This file
├── CITATION.cff  # Citation metadata for Zenodo / Google Scholar
└── LICENSE       # MIT License
```

---

## Relation to DonatJS Ecosystem

SVG.js was developed as the icon vocabulary layer for applications built with [DonatJS](https://github.com/ktupad/donat) — a JSON-driven MVC web framework for Indonesian educational institutions. The `di-` class prefix mirrors the `bi-` convention from Bootstrap Icons, ensuring familiarity while remaining completely independent.

**Generation lineage:**

| Year | Project  | Paradigm              | HKI / IP           |
|------|----------|-----------------------|--------------------|
| 2019 | Ktupad   | MVC PHP               | EC00201952487      |
| 2023 | BayamJS  | MVC JavaScript        | EC00202367008      |
| 2024 | DonatJS  | JSON-driven MVC       | EC00202414144      |
| 2024 | SVG.js   | JSON-driven SVG engine| (this repository)  |

---

## Academic Background

SVG.js is grounded in peer-reviewed literature across four domains:

### SVG Rendering & DOM Performance

The inline SVG approach adopted by SVG.js — where icons are injected directly into the DOM via `svg.di()` — is informed by research on SVG rendering efficiency. Schwab et al. (2022) demonstrate that SVG is the dominant markup language for web visualizations due to its openness, CSS customizability, and full DOM searchability, while also identifying rendering bottlenecks that motivate lean, path-only implementations such as the one used in SVG.js (DOI: [10.1109/TVCG.2021.3059294](https://doi.org/10.1109/TVCG.2021.3059294)).

### SVG Accessibility

The `di-{key}` class-based injection pattern in SVG.js is designed to be compatible with accessibility best practices for SVG on the web. Zhang et al. (2023) specifically address the automation of accessible alternative text for SVG buttons on web pages, underscoring the importance of structured, programmatic SVG delivery — the exact approach taken by `svg.di()` (DOI: [10.1016/j.eswa.2023.120836](https://doi.org/10.1016/j.eswa.2023.120836)).

### Front-End Performance Optimization

SVG.js eliminates HTTP overhead by embedding all icon paths in a single JavaScript file, avoiding external requests for icon fonts or image assets. This design is supported by Riet et al. (2023), who provide industrial evidence that reducing front-end asset complexity yields measurable performance improvements (DOI: [10.1016/j.jss.2022.111593](https://doi.org/10.1016/j.jss.2022.111593)), and by Ekpobimi et al. (2024), who frame code splitting, lazy loading, and minification as essential strategies for optimizing performance across heterogeneous device and network environments (DOI: [10.58175/gjarr.2024.2.1.0032](https://doi.org/10.58175/gjarr.2024.2.1.0032)).

### Resource-Constrained Educational Environments

SVG.js is designed for deployment in Indonesian educational web applications where bandwidth and device capability may be limited. This context is directly addressed by Okai-Ugbaje et al. (2022), who establish a framework for mobile and web learning tools suited to resource-constrained higher education environments (DOI: [10.1007/s10639-022-11094-5](https://doi.org/10.1007/s10639-022-11094-5)), and by Kynge (2020), who identifies the need for lightweight, locally relevant, and offline-capable digital educational content in low-resource settings (DOI: [10.2196/16946](https://doi.org/10.2196/16946)). Infrastructure and adoption barriers specific to developing countries, including Indonesia, are documented by Madni et al. (2022) (DOI: [10.3389/fpsyg.2022.915596](https://doi.org/10.3389/fpsyg.2022.915596)).

---

## References

1. Schwab, M., Saffo, D., Bond, N., Sinha, S., Dunne, C., Huang, J., Tompkin, J., & Borkin, M. A. (2022). Scalable Scalable Vector Graphics: Automatic Translation of Interactive SVGs to a Multithread VDOM for Fast Rendering. *IEEE Transactions on Visualization and Computer Graphics*, 28(9), 3219–3234. https://doi.org/10.1109/TVCG.2021.3059294

2. Zhang, M., Zhang, Y., Gao, G., & Liu, H. (2023). Enhancing accessibility of web-based SVG buttons: An optimization method and best practices. *Expert Systems with Applications*, 231, 120836. https://doi.org/10.1016/j.eswa.2023.120836

3. Riet, J., Malavolta, I., & Ghaleb, T. (2023). Optimise along the way: An industrial case study on web performance. *Journal of Systems and Software*, 198, 111593. https://doi.org/10.1016/j.jss.2022.111593

4. Ekpobimi, H. O., Kandekere, R. C., & Fasanmade, A. A. (2024). Conceptual Framework for Enhancing Front-end Web Performance: Strategies and Best Practices. *Global Journal of Advanced Research and Reviews*, 2(1), 099–107. https://doi.org/10.58175/gjarr.2024.2.1.0032

5. Okai-Ugbaje, S., Ardzejewska, K., & Imran, A. (2022). A mobile learning framework for higher education in resource constrained environments. *Education and Information Technologies*, 17(7), 3975–3999. https://doi.org/10.1007/s10639-022-11094-5

6. Kynge, L. (2020). Finding the Best Way to Deliver Online Educational Content in Low-Resource Settings: Qualitative Survey Study. *Journal of Medical Internet Research*, 22(5), e16946. https://doi.org/10.2196/16946

7. Madni, S. H. H., Ali, J., Husnain, H. A., Masum, M. H., Mustafa, S., Shuja, J., Maray, M., & Hosseini, S. (2022). Factors Influencing the Adoption of IoT for E-Learning in Higher Educational Institutes in Developing Countries. *Frontiers in Psychology*, 13, 915596. https://doi.org/10.3389/fpsyg.2022.915596

---

## Citation

If you use SVG.js in academic work, please cite:

```bibtex
@software{sismadi_svgjs_2024,
  author    = {Sismadi, Wawan},
  title     = {{SVG.js: A Lightweight JSON-Driven SVG Icon Rendering Engine}},
  year      = {2024},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.XXXXXXX},
  url       = {https://github.com/ktupad/svg}
}
```

See `CITATION.cff` for full metadata.

---

## License

MIT License © 2024 Wawan Sismadi / PT Sismadi Langit Solusi

Permission is hereby granted, free of charge, to any person obtaining a copy of this software to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.

---

## Author

**Wawan Sismadi**  
NIDN: 0816087703 | SINTA ID: 6848496 | ORCID: [0009-0007-2685-5663](https://orcid.org/0009-0007-2685-5663)  
Lecturer, Universitas IPWIJA · Doctoral Candidate, Universitas Ahmad Dahlan  
Founder, PT Sismadi Langit Solusi  

> *"Saya menciptakan standar baru untuk web Indonesia."*
