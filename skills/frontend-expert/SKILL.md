---
name: frontend-expert
description: Use when building UI components, optimizing frontend performance, implementing responsive design, or setting up frontend architecture — especially when encountering CLS issues, large bundle sizes, or accessibility violations flagged by Lighthouse/axe.
---
# Frontend Expert Skill

Expert in modern frontend development, UI/UX design, and performance optimization.

## When to Use
- Building UI components and pages with Angular, React, Vue, or Svelte
- Optimizing Core Web Vitals and bundle size
- Implementing responsive, accessible (a11y) designs
- Setting up frontend project architecture and tooling

## When NOT to Use
- Backend API or service design (use backend-architect)
- Infrastructure or deployment concerns only (use cicd-automation or cloud-infrastructure)

## Quick Reference
| Situation | Action |
|-----------|--------|
| Building new page | Design responsive layout first, implement with reusable components |
| Slow page loads | Check Core Web Vitals, lazy load below-fold content, tree-shake bundles |
| a11y violations | Run axe/Lighthouse, fix semantic HTML, add ARIA labels |

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

## Common Mistakes
- **Ignoring bundle size**: Importing entire libraries instead of tree-shakeable subsets bloats bundles.
- **Accessibility as an afterthought**: Adding a11y after build is 10x harder than designing for it from the start.
- **Missing loading/error states**: Assuming API calls always succeed leaves users staring at blank screens.

## Cross-References
- **RECOMMENDED:** security-auditor — CSP headers, XSS prevention, and secure data handling.
- **RECOMMENDED:** backend-architect — API contract alignment between frontend and backend.

## Must Not Do
- NEVER use `dangerouslySetInnerHTML` or `innerHTML` without sanitization.
- NEVER block the main thread with long-running synchronous scripts.
- NEVER hardcode API URLs, secrets, or feature flags in client-side code.
