# Portfolio Redesign Instructions: Nick Warshak

## 1. Visual Identity & Inspiration
The goal is a "Premium Professional" aesthetic. 
- **Inspiration A (Explora Journeys):** Utilize thin borders, expansive white space, and a refined color palette (midnight blues, soft creams, or slate grays). Use serif headings for a "magazine" feel.
- **Inspiration B (Urbanex Next21):** Incorporate bold, oversized typography and a rigid, modern grid. Transitions should feel "weighty" and smooth.

## 2. Component: The "Looping Showcase"
Create a high-performance, infinite-looping horizontal slider for project screenshots.
- **Behavior:** The track should move at a slow, constant speed. On hover, the movement should pause or slow down significantly.
- **Styling:** Screenshots should have a subtle drop shadow or "floating" effect. Use a container with `overflow: hidden` and absolute positioning for the duplicate track to ensure a seamless loop.
- **Content:** This will feature work including 'Margin Command', the NFL Prediction Engine, and 'Jane & Rye LLC' branding.

## 3. Professional Context for Content Generation
When generating placeholder text or project descriptions, use the following context:
- **Title:** Data Systems & AI Specialist.
- **Education:** Lindner College of Business (Information Systems & Computer Science). 
- **Current Role:** Data systems and analysis at Jake Sweeney Kia.
- **Upcoming:** AI Internship at Paychex (Summer 2026).
- **Core Interests:** Artificial Intelligence, Machine Learning, and Cloud Infrastructure.

## 4. Technical Constraints
- **Framework:** Maintain the current Hugo structure but modernize the layouts using Tailwind CSS or custom CSS variables.
- **Interactivity:** Use Framer Motion or GSAP for entrance animations (fade-up, staggered reveals).
- **Performance:** Prioritize image optimization for the looping screenshots to ensure zero layout shift.

## 5. Iteration Loop
- When I provide a screenshot of a specific UI element I like, analyze the padding, font-weight, and color hex codes precisely.
- Always check for mobile responsiveness; the luxury aesthetic must translate to a clean, single-column view.