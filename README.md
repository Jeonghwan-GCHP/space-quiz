# 🌌 Space Quiz

A fun and educational Korean-language space exploration quiz built with vanilla HTML, CSS, and JavaScript. No build tools or external dependencies required!

## Features

✨ **10 Interactive Questions** - Test your knowledge about space and astronomy
🎨 **Beautiful UI** - Modern design with light and dark mode support
📱 **Fully Responsive** - Works seamlessly on desktop, tablet, and mobile devices
⚡ **Zero Dependencies** - Pure vanilla JavaScript, no frameworks needed
🎯 **Instant Feedback** - Immediate visual feedback for correct and incorrect answers
📊 **Score Tracking** - Track your performance with emoji-based reactions

## Demo

[Play the Space Quiz online](https://jeonghwan-gchp.github.io/space-quiz/)

## Local Setup

Since this is a single-file application with no build process, you can run it immediately:

### Option 1: Direct Browser Opening
1. Clone the repository:
   ```bash
   git clone https://github.com/Jeonghwan-GCHP/space-quiz.git
   cd space-quiz
   ```
2. Open `index.html` directly in your browser:
   - **macOS/Linux**: `open index.html` or `xdg-open index.html`
   - **Windows**: Double-click `index.html`
   - Or drag `index.html` into your browser window

### Option 2: Using a Local Server (Recommended)
For better development experience, serve the file locally:

```bash
# Using Python 3
python -m http.server 8000

# Using Python 2
python -m SimpleHTTPServer 8000

# Using Node.js (if you have http-server installed)
npx http-server

# Using Ruby
ruby -run -ehttpd . -p8000
```

Then open `http://localhost:8000` in your browser.

## How to Play

1. **Answer Questions** - Click on one of the four options for each question
2. **Get Instant Feedback** - Correct answers turn green with a pulse animation; incorrect answers turn red with a shake animation
3. **Track Your Progress** - Watch the progress bar fill as you complete questions
4. **View Results** - After all 10 questions, see your final score with an emoji-based reaction
5. **Try Again** - Click "다시 시작" (Restart) to retake the quiz

## Scoring

- **100%** (10/10): 🌟 완벽합니다! 당신은 우주 전문가입니다!
- **80-99%** (8-9/10): 🚀 훌륭합니다! 우주에 대해 아주 잘 알고 있네요.
- **60-79%** (6-7/10): 🌍 좋습니다! 더 배울 수 있을 것 같아요.
- **40-59%** (4-5/10): 🌙 조금 더 노력해보세요!
- **<40%** (0-3/10): 🔭 우주 탐사를 계속해보세요!

## Architecture

The entire application is contained in a single `index.html` file (~15KB):

- **HTML** (lines 381+) - Page structure and quiz content
- **CSS** (lines 7-379) - Styling, animations, and responsive design
- **JavaScript** (lines 490+) - Quiz logic and state management

### Key Features

- **Responsive Design** - Adapts to screen sizes from mobile (480px) to desktop
- **Dark Mode Support** - Automatically follows system color scheme preference
- **Accessibility** - Keyboard navigation with focus management
- **Smooth Animations** - Visual feedback with CSS keyframes (pulse, shake, bounce)
- **State Management** - Pure JavaScript without external libraries

## Customization

To modify the quiz questions:

1. Open `index.html` in your text editor
2. Find `const quizData = [` around line 490
3. Edit, add, or remove questions following this format:
   ```javascript
   {
     question: "우주에서 가장 큰 행성은?",
     options: ["지구", "목성", "토성", "해왕성"],
     correct: 1  // Index of the correct option (0-3)
   }
   ```
4. **Important**: Keep exactly 10 questions for proper score calculation
5. Save and refresh your browser

## Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

Requires ES6+ support and CSS Grid/Flexbox.

## Development

No build tools or test runners needed! For development:

1. Edit `index.html` in your preferred text editor
2. Open in browser to test changes immediately
3. Check dark mode by toggling system color scheme
4. Test responsive design by resizing browser or using device emulation

### Manual Testing Checklist

- [ ] First question loads with 4 options
- [ ] Correct answer turns green and increments score
- [ ] Wrong answer turns red and shows correct answer in green
- [ ] Progress bar fills as questions are answered
- [ ] All 10 questions display correctly
- [ ] Results screen shows with emoji reaction
- [ ] Restart button resets quiz
- [ ] Tab key navigates between options
- [ ] Dark mode colors are readable

## Deployment

This static HTML file can be deployed anywhere:

- **GitHub Pages** - Automatic via GitHub Actions (configured)
- **Netlify** - Drag and drop deployment
- **Vercel** - Git-based deployment
- **AWS S3 + CloudFront** - Static hosting
- **Any web server** - Just serve the HTML file

## License

This project is open source and available under the MIT License.

## Author

Created by [Jeonghwan-GCHP](https://github.com/Jeonghwan-GCHP)

---

**Happy learning! 🚀🌌**
