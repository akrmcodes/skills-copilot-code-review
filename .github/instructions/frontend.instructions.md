---
applyTo: "*.html,*.css,*.js"
---

## Frontend Guidelines

### HTML Structure & Accessibility
- Use semantic HTML elements: `<header>`, `<nav>`, `<main>`, `<section>`, `<aside>`, `<footer>`, etc.
- Include `alt` attributes on all images and icons
- Use `aria-label` for icon buttons and non-obvious controls (e.g., search button)
- Include meaningful `id` and `class` attributes for styling and JavaScript targeting

### Responsive Design
- Design mobile-first: styles should work at 320px width and scale up
- Use media queries for tablet (768px) and desktop (1024px+) breakpoints
- Test layout on multiple screen sizes to ensure usability
- Ensure buttons and interactive elements are large enough for touch (min 44px)

### JavaScript & API Integration
- API root: `/` (e.g., `/activities`, `/auth/login`)
- Handle error responses gracefully—show user-friendly error messages, not implementation details
- Show loading states during API calls
- Validate user input before sending to server
- Never expose sensitive data (tokens, passwords) in console logs or error messages

### User State Management
- User login state stored in DOM: `user-controls`, `user-status`, `user-info` elements
- Show/hide login button and user info dynamically based on session
- Clear user state on logout and reset UI to initial state

### Styling Patterns
- CSS file: `styles.css` (referenced in `index.html`)
- Use consistent color scheme, fonts, and spacing throughout
- Maintain visual hierarchy with clear typography
- Prefer CSS variables for reusable colors and spacing values

### Frontend-Backend Sync
- Consult API documentation at `/docs` when in doubt about endpoint responses
- Changes to backend response formats require corresponding frontend updates
- Test API calls using FastAPI's interactive docs before assuming correctness