# Copilot Instructions for Space Quiz

## Project Overview

This is a **single-file Korean-language space exploration quiz** built with vanilla HTML/CSS/JavaScript. No build tools, server, or external dependencies required. The application is fully self-contained in `index.html` and can run directly in any modern browser.

## Architecture

### Single-File Structure
The entire application consists of one HTML file with three integrated sections:

1. **HTML (lines 381+)** - Page structure, quiz content area, results screen
2. **CSS (lines 7-379)** - All styling, animations, color schemes, responsive design
3. **JavaScript (lines 490+)** - Quiz logic, state management, event handlers

### Core Components

#### Quiz State Management
- `quizData` - Array of 10 question objects with `question`, `options[]`, and `correct` (index of right answer)
- `currentQuestion` - Current question index (0-9)
- `score` - Running point total (increments by 10 per correct answer)
- `correct` - Count of correct answers (used for results calculation)
- `answered` - Boolean flag to prevent multiple selections per question

#### Key Functions
- `init()` - Resets all state variables, shows quiz, hides results
- `loadQuestion()` - Renders current question, updates progress bar, auto-focuses first option
- `selectOption(selectedIndex, correctIndex)` - Handles answer selection, applies animations, updates score
- `showResults()` - Hides quiz, displays results screen with emoji reaction based on score percentage

#### Animation Classes
- `.correct` - Green background + pulse (0.4s) on right answer
- `.incorrect` - Red background + shake (0.5s) on wrong answer
- `.disabled` - Applied to all options after answering to prevent re-selection

### Design System

#### CSS Variables (Light/Dark)
```css
:root {
  --primary: #6366f1           /* Indigo - main accent */
  --success: #10b981           /* Green - correct answers */
  --error: #ef4444             /* Red - incorrect answers */
  --bg-light: #f8fafc / #0f172a (dark)
  --bg-white: #ffffff / #1e293b (dark)
  --text-dark: #1e293b / #f1f5f9 (dark)
  --text-gray: #64748b / #cbd5e1 (dark)
  --border: #e2e8f0 / #334155 (dark)
}
```

#### Layout Constraints
- Max-width: 500px (narrow column, centered)
- Viewport height: 100vh (full screen)
- System font stack: `-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
- Base font size: 15px (within 14-16px body text range)
- Mobile breakpoint: 480px (adjust padding, font sizes)

#### Key Styling Patterns
- **Mission-Control Score Display**: Gradient border, glow effect, monospace font with diamond icons
- **Progress Bar**: Linear gradient fill, smooth 0.3s transition
- **Animations**: All use `ease-out` timing; durations 0.3s-0.6s
- **Feedback**: Color + animation (not color-only, for accessibility)

## Conventions

### Question/Answer Format
Each question in `quizData` follows this structure:
```javascript
{
  question: "Question in Korean",
  options: ["Option 0", "Option 1", "Option 2", "Option 3"],
  correct: 1  // Index (0-3) of the correct option
}
```
- Always 4 options per question
- `correct` must be 0-3 (array index)
- Questions must be Korean

### Results Scoring Tiers
- **100%** (10/10): 🌟 "완벽합니다! 당신은 우주 전문가입니다!"
- **80-99%** (8-9/10): 🚀 "훌륭합니다! 우주에 대해 아주 잘 알고 있네요."
- **60-79%** (6-7/10): 🌍 "좋습니다! 더 배울 수 있을 것 같아요."
- **40-59%** (4-5/10): 🌙 "조금 더 노력해보세요!"
- **<40%** (0-3/10): 🔭 "우주 탐사를 계속해보세요!"

### Timing Constants
- **Answer-to-next-question delay**: 1200ms (`setTimeout(..., 1200)`)
- **Animation durations**: 0.3s-0.6s (see CSS keyframes)
- **Progress updates**: Immediate, no delay

### Color Usage
- **Green (#10b981)** - Correct answers only
- **Red (#ef4444)** - Incorrect answers only
- **Indigo (#6366f1)** - Primary UI elements, progress bar, borders
- **Ensure dark mode contrast**: All colors have dark-mode equivalents in `@media (prefers-color-scheme: dark)`

### Accessibility Requirements
- **Focus management**: First option auto-focuses on question load
- **Semantic HTML**: Options are `<button>` elements, not divs
- **No color-only feedback**: Green/red backgrounds paired with animations
- **WCAG contrast**: Text meets AAA standards in both light/dark modes

## Development Workflow

### Editing Questions
1. Locate `const quizData = [` (around line 490)
2. Modify, add, or remove question objects
3. **Important**: Keep exactly 10 questions for score calculation (scores are `correct/10 * 100%`)
4. Test in browser: open `index.html` directly (no server needed)

### Modifying Styling
1. All CSS is in `<style>` tags (lines 7-379)
2. CSS variables defined in `:root` and `@media (prefers-color-scheme: dark)`
3. Update variables for theme changes; use them in rules for consistency
4. Test dark mode by toggling OS color scheme setting
5. Test mobile at 480px breakpoint

### Adding Features
- **New animations**: Add `@keyframes` block, apply via class (see `.pulse`, `.shake`, `.bounce`)
- **New pages/states**: Use `.show`/`.hidden` classes to toggle visibility
- **Score adjustments**: Edit `score += 10` in `selectOption()` function
- **Results logic**: Update emoji/message tiers in `showResults()` function

### Testing in Browser
```bash
# No build step needed - just open the file directly
open /Users/jh/GCHP_Dev_Days/space-quiz/index.html
# Or from browser address bar: file:///Users/jh/GCHP_Dev_Days/space-quiz/index.html
```

**Manual smoke test checklist:**
- [ ] First question loads with 4 options
- [ ] Clicking correct answer: green + pulse, score increments by 10
- [ ] Clicking wrong answer: red shake, correct shown in green, score unchanged
- [ ] Progress bar fills as you answer questions
- [ ] After Q10: results screen shows with score and emoji
- [ ] Restart button reloads page and resets score to 0
- [ ] Tab key navigates between options
- [ ] Dark mode colors are readable and properly contrasted

## File Structure

```
/space-quiz/
├── index.html                      # Single app file (15KB, 610 lines)
└── .github/
    └── copilot-instructions.md     # This file
```

## No Build/Test Commands

This project requires no build tools, package managers, linters, or test runners. It is a static HTML file designed for immediate browser deployment.

- **Development**: Edit `index.html` directly
- **Testing**: Open in browser, manually verify features
- **Deployment**: Copy `index.html` to web server (or serve via CDN)

## Language & Localization

- **Primary language**: Korean (한글)
- All user-facing text (questions, results, buttons, labels) must be Korean
- Metadata (comments, variable names) can be English
- Font stack includes Korean character support via system fonts

## Browser Compatibility

- Targets: Chrome, Safari, Firefox, Edge (modern versions)
- ES6+ syntax supported (arrow functions, template literals, const/let)
- CSS Grid/Flexbox supported
- `prefers-color-scheme` media query supported
- No polyfills needed

## Deployment

The single `index.html` file is production-ready with zero dependencies:
1. Copy `index.html` to your web server or static hosting
2. No build step, no environment variables, no configuration files
3. File can be opened locally (`file://`) or served over HTTP/HTTPS
