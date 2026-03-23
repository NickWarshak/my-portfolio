---
title: "Professional Portfolio Website"
date: 2026-02-05
draft: false
description: "A fully custom Hugo static site with a hand-built design system, deployed via GitHub Actions."
tags: ["Hugo", "GSAP", "CSS", "GitHub Actions", "CI/CD"]
Weight: 100
---
[View the Source Code on GitHub](https://github.com/NickWarshak/my-portfolio)

### Project Overview
Designed and built a professional portfolio site from scratch using Hugo — no theme dependency. The entire visual design system was hand-written in a single CSS file using custom properties, fluid typography, and a light/dark mode toggle. Interactive animations are powered by GSAP with ScrollTrigger for scroll-based reveals.

---

### Technical Stack
* **Framework:** Hugo (Static Site Generator)
* **Design:** Custom CSS design system — zero framework or theme dependency
* **Typography:** Cormorant Garamond (display) + Inter (UI), loaded via Google Fonts
* **Animation:** GSAP 3.12 + ScrollTrigger
* **Deployment:** GitHub Actions → GitHub Pages (automated on push to main)

---

### Key Features & Implementation
* **Custom Design System:** Built a complete set of CSS custom properties for color tokens, spacing, and typography — supporting seamless light/dark mode switching via a `data-theme` attribute and `localStorage`.
* **Infinite Slider:** Engineered a CSS `@keyframes marquee` loop with two duplicate tracks for a seamless, performant scroll. Pause-on-hover handled in vanilla JS.
* **GSAP Animations:** Hero entrance animations on load, scroll-triggered fade-up reveals for below-fold content via `IntersectionObserver` fallback.
* **Hugo Pipes:** CSS is fingerprinted at build time for cache-busting. GitHub Actions passes the correct `--baseURL` from `configure-pages` output to ensure all links resolve correctly on GitHub Pages.
* **No PaperMod:** Previous version used PaperMod theme with CSS overrides. Fully replaced with a custom `baseof.html`, `list.html`, `single.html`, and partials for complete design control.

---

### Why it Matters
This project demonstrates end-to-end ownership of a production web product — from information architecture and visual design to CI/CD pipeline configuration and URL routing on a subdirectory-hosted GitHub Pages deployment.
