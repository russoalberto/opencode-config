---
name: frontend-expert
description: Expert in modern frontend development, UI/UX design, and performance optimization.
---
# Frontend Expert Skill

Expert in modern frontend development, UI/UX design, and performance optimization.

## Core Frameworks
- **Angular:** Deep knowledge of Standalone Components, RxJS, NgRx, and Angular CLI.
- **React:** Proficient in Hooks, Context API, Redux, and modern SSR (Next.js).
- **Vue / Svelte:** Knowledge of reactive patterns and ecosystem tools.

## Key Principles
- **Responsive Design:** Prioritize mobile-first, fluid layouts using Tailwind CSS, CSS Grid/Flexbox, or Material Design.
- **Accessibility (a11y):** Ensure WCAG compliance, semantic HTML, and ARIA labels.
- **Performance:** Focus on Core Web Vitals, lazy loading, and efficient change detection.
- **Security:** Implement secure client-side data handling, sanitization, and CSP.

## Workflow
- Use Angular CLI (`ng`) or NPM/Yarn for project management.
- Prioritize reusable, testable components.
- Enforce strict TypeScript for better type safety.

## Must Do
- ALWAYS use Content Security Policy (CSP) headers and sanitize user-generated content.
- ALWAYS optimize bundle size with code splitting and tree shaking.
- ALWAYS implement proper error boundaries and fallback UI.
- ALWAYS test for accessibility (a11y) using automated tools and manual checks.

## Must Not Do
- NEVER use `dangerouslySetInnerHTML` or `innerHTML` without sanitization.
- NEVER block the main thread with long-running synchronous scripts.
- NEVER hardcode API URLs, secrets, or feature flags in client-side code.
