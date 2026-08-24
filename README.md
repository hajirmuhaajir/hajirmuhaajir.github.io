# Hajir Studio

![Status](https://img.shields.io/badge/status-active-success.svg)
![Type](https://img.shields.io/badge/type-client--side%20static%20site-blue.svg)
![Tech](https://img.shields.io/badge/tech-HTML5%20%7C%20CSS3%20%7C%20JavaScript%20%7C%20Tailwind%20CSS-purple.svg)
![License](https://img.shields.io/badge/license-all%20rights%20reserved-lightgrey.svg)

A personal portfolio and tool hub for Hajir Stein (Haiere), showcasing web development projects, free digital tools, and a music collection.

---

## Overview

Hajir Studio is a single-page portfolio website that serves as the personal hub for Hajir Stein, a web developer and musician. It presents a curated collection of free, privacy-first web tools, original music releases, and a contact channel.

The website is fully client-side, with no backend dependencies. It features a glassmorphism design, dark/light theme support, bilingual content in Indonesian and English, and a responsive layout optimised for all screen sizes.

---

## Features

- Tool directory — a curated list of free web tools including HajirSync, Raia Vault, Raia Scrub, Raia Delta, Raiamify, Raia AI, Calc, and Chess.
- Music showcase — embedded Signature Music player for streaming original tracks.
- Quote collection — a selection of inspirational quotes relevant to the creator’s philosophy.
- Contact form — integrated with Formspree for message submissions.
- Language toggle — switch between Indonesian and English translations across all text content.
- Dark/light theme — manual toggle with system preference detection and persistent storage.
- Glassmorphism UI — Apple-inspired design with backdrop blur, subtle shadows, and smooth hover animations.
- Interactive visual effects — spotlight cursor effect on the hero section, tilt cards, and magnetic button animations for non-touch devices.
- Accessibility support — skip link, ARIA attributes, keyboard navigation, and reduced-motion preferences.
- Privacy-first analytics — uses Plausible Analytics for lightweight, cookieless traffic measurement.

---

## Requirements

- A modern web browser with JavaScript enabled, such as Chrome, Firefox, Edge, Safari, or similar.
- Internet access to load:
  - Google Fonts: Inter, Outfit, JetBrains Mono.
  - Font Awesome icons.
  - Tailwind CSS via CDN.
  - Plausible Analytics script.
- A working Formspree endpoint.

---

## Installation

Hajir Studio is a single HTML file with associated CSS and JavaScript assets. To use it:

1. Open the hosted URL in your browser.
2. Alternatively, download `index.html` and the associated assets (`icons.js`, `script.js`, `style.css`) and open `index.html` locally.

To host the website yourself, place the files on any static web server.

---

## Usage

### Navigation

The header provides a logo, theme toggle, and a menu button that opens a side drawer with navigation links.

The side drawer lists the main sections:
- About.
- Music.
- Quotes.
- Tools.
- Contact.

It also includes language selection, a GitHub link, a RAIA AI link, and legal footer links.

### Sections

| Section | Description |
|---|---|
| Hero | Introduces Hajir with a tagline, call-to-action buttons, and a scrolling ticker of keywords. |
| About | Shows biographical information, role tags, and statistics such as tools released, music releases, original songs, and privacy commitment. |
| RWR-AMA | A dedicated promotional card linking to a related project. |
| Music | Embedded Signature Music player for streaming original tracks. |
| Quotes | A grid of four inspirational quotes with author attribution. |
| Tools | A filterable list of free web tools with descriptions and “Open Tool” buttons. Each tool also includes a documentation button that opens a modal with usage instructions. |
| Contact | A contact form with validation, submission status, and a fallback message with social media links. |
| Footer | Logo, tagline, social media links, footer navigation, and legal disclaimers. |

---

## Available Tools

| Tool | Category | Description |
|---|---|---|
| HajirSync | Music | Generate synchronised LRC lyric files. |
| Raia Vault | Security | Generate strong random passwords. |
| Raia Scrub | Security | Remove sensitive metadata, such as GPS data, from photos. |
| Raia Delta | Web | Compare two blocks of text and highlight their differences. |
| Raiamify | Web | A lightweight AI tool for fast assistance. |
| Raia AI | Web | AI platform supporting multiple providers. |
| Calc | Web | A simple, fast calculator. |
| Chess | Web | Classic chess game. |

---

## Configuration

### Language

- The language toggle in the side drawer switches all text content between Indonesian and English.
- The selected language is stored in `localStorage` and persists across sessions.
- The default language is determined by `navigator.language`, with Indonesian or English as the fallback.

### Theme

- The theme toggle switches between dark and light modes.
- The default theme follows system preference via `prefers-color-scheme`.
- The selected theme is stored in `localStorage`.

### Cookie consent

- A cookie banner appears on first visit, offering Accept or Reject options.
- Acceptance stores a cookie consent flag in `localStorage`.
- The banner is for functional consent only; Plausible Analytics is cookieless and does not require cookies or persistent identifiers [web:17][web:22][web:24].

---

## Project Structure

```text
/
├── index.html          # Main HTML file
├── style.css           # Custom CSS (glassmorphism, animations, utilities)
├── script.js           # Main JavaScript (navigation, theme, i18n, form, animations)
├── icons.js            # SVG icon definitions used across the site
└── manifest.webmanifest # Web app manifest for PWA support
```

---

## Examples

### Adding a new tool

To add a new tool to the directory:

1. Add a new `<li>` element to `#tools-container` with the `tool-card` class.
2. Set the `data-category` attribute to an existing category (`music`, `security`, `web`).
3. Add `data-i18n` attributes for title and description.
4. Add translations for the new keys in the `i18n` object in `script.js`.
5. Add the tool’s documentation content as a separate markdown file in the repository, referenced by the `data-repo` attribute.

### Adding a new translation

1. Locate the `i18n` object in `script.js`.
2. Add a new language key, such as `fr`.
3. Copy the `id` or `en` object and translate all string values.
4. The language toggle will automatically recognise the new key.

---

## Troubleshooting

- Contact form does not send — ensure the Formspree endpoint is valid. The form uses `https://formspree.io/f/mpqkqanp`. If it fails, check the browser console for errors.
- Theme not persisting — check that your browser allows `localStorage` and that you are not in private or incognito mode.
- Language not switching — ensure JavaScript is enabled. The language toggle updates all `data-i18n` and `data-i18n-placeholder` elements.
- Music player does not load — the player is embedded via an iframe pointing to `https://haiere.github.io/signature-music`. If the page fails to load, the fallback link below the player provides a direct link.
- Documentation modal does not open — ensure the `data-repo` attribute on the tool card matches a valid repository path. The modal attempts to fetch `https://raw.githubusercontent.com/haiere/[repo]/main/README.md`.

---

## Privacy and Security

- No personal data is stored on any server; all user data remains in the browser’s `localStorage`.
- Contact form submissions are processed via Formspree. Data is not stored on this site’s server.
- Plausible Analytics is used for lightweight aggregate traffic measurement and does not use cookies or personal identifiers [web:21][web:22][web:24].
- External services include GitHub, Instagram, SoundCloud, Reddit, X, Quora, and Discord. Each platform operates under its own privacy policy.

---

## Development

The application is a single HTML file with linked CSS and JavaScript files. To modify or extend it:

- Edit `index.html` for structure.
- Edit `style.css` for styles.
- Edit `script.js` for functionality.
- Edit `icons.js` for SVG icon definitions.

The site uses Tailwind CSS via CDN, with a custom configuration for dark mode and extended font families.

---

## License

This website and its content are the property of Haiere. All rights reserved. For licensing inquiries, contact via the website.

---

## Author

Developed by HajirStudio — a web developer, AI builder, and musician.

---

## Last Updated

2026