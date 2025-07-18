# Copilot Instructions for Shiny Stone

## Project Overview
This is a educational HTML/JavaScript project for learning web development with kids. The project consists of standalone HTML files demonstrating progressive web development concepts from basic HTML to interactive JavaScript applications.

## Project Structure
- `index.html` - Main navigation page linking to all demo files
- `simple.html` - Basic HTML structure tutorial
- `style.html` - CSS styling demonstration with embedded styles
- `circle.html` - Interactive JavaScript demo (click-to-draw circles)
- `2fingers.html` - Advanced touch-based timer game with localStorage
- `timer-app.html` - Universal timer app with leaderboard (PC/mobile, landscape/portrait)
- `flo1.html` & `flo2.html` - Student work/experiments
- `rubiks1.png` - Static asset for Rubik's cube timer project

## Key Patterns & Conventions

### File Organization
- Each HTML file is completely self-contained with embedded CSS/JS
- No external dependencies or build process
- Files follow a progressive complexity model: HTML → CSS → JavaScript → Touch APIs → Universal Apps

### CSS Patterns
- Embedded `<style>` tags in document head
- CSS comments explain styling choices for educational purposes
- Common color scheme: light blues (`#f0f8ff`, `dodgerblue`) and dark grays (`#333366`, `#555555`)
- Responsive design considerations in advanced files (`2fingers.html`, `timer-app.html`)
- Universal apps use flexbox and viewport units for cross-device compatibility

### JavaScript Patterns
- Vanilla JavaScript only - no frameworks or libraries
- Event-driven programming with `addEventListener`
- DOM manipulation using `document.createElement` and `appendChild`
- Local storage for persistence: `localStorage.getItem/setItem`
- Touch event handling for mobile: `touchstart`, `touchend`
- Universal input handling: supports both mouse and touch events for cross-platform compatibility

### Development Approach
- **Educational Focus**: Code includes extensive comments explaining concepts
- **Progressive Complexity**: Each file builds on previous concepts
- **Mobile-First**: Advanced demos (`2fingers.html`) designed for touch interfaces
- **Universal Design**: Latest apps (`timer-app.html`) work across all devices and orientations
- **No Build Process**: Direct file serving - open HTML files in browser

## Timer App Pattern (`timer-app.html`)
The universal timer app demonstrates cross-platform development patterns:
- **Universal Input**: Handles both mouse (PC) and touch (mobile) events for press/release
- **Responsive Layout**: Uses flexbox and viewport units to work in landscape/portrait
- **State Management**: Simple state machine for timer states (idle, running, stopped)
- **Leaderboard Integration**: localStorage-based scoring with CRUD operations
- **Visual Feedback**: Large, centered timer display with blue color scheme

## Common Tasks

### Adding New Demos
1. Create self-contained HTML file with embedded CSS/JS
2. Add educational comments explaining new concepts
3. Update `index.html` navigation list
4. Follow naming convention: descriptive, lowercase with hyphens

### Testing
- Open files directly in browser (no server required)
- Test on mobile devices for touch-based demos
- Verify localStorage persistence across browser sessions

### Debugging
- Use browser developer tools console for JavaScript errors
- Check responsive design at different screen sizes
- Validate HTML structure and CSS rendering

## Key Files for Reference
- `circle.html` - Example of DOM manipulation and event handling
- `2fingers.html` - Advanced touch API usage and localStorage patterns
- `timer-app.html` - Universal app design with cross-platform input handling
- `style.html` - CSS organization and commenting conventions
