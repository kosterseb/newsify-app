# Newsify

A modern, mobile-first news application built with React and powered by The New York Times API. Stay informed with the latest news across multiple categories including Health, Sports, Business, Travel, and World news.

![Newsify App](https://kosterseb.github.io/newsify-app)

## Features

### Core Functionality
- **Browse News by Category** - Access curated news from Health, Sports, Business, Travel, and World sections
- **Search Articles** - Find specific news articles with the built-in search functionality
- **Archive System** - Save articles to your personal archive with swipe gestures
- **Dark Mode** - Toggle between light and dark themes for comfortable reading
- **Category Management** - Show/hide news categories based on your interests
- **Pull-to-Refresh** - Update your news feed with a simple pull-down gesture

### User Experience
- **Onboarding Flow** - First-time user tutorial with smooth animations
- **Splash Screen** - Animated logo and brand introduction
- **Swipe Gestures** - Intuitive left/right swipes to archive or delete articles
- **Expandable Categories** - Collapse/expand news categories for better organization
- **Persistent Settings** - Your preferences are saved locally across sessions

## Tech Stack

- **React 19** - Modern UI library with hooks and context
- **React Router 7** - Client-side routing (migrated from deprecated react-router-dom)
- **Vite** - Lightning-fast build tool and dev server
- **Sass** - CSS preprocessor with nested rules and variables
- **Vitest** - Unit testing framework
- **The New York Times API** - Real-time news data
- **GitHub Actions** - Automated deployment pipeline
- **GitHub Pages** - Static site hosting

## Getting Started

### Prerequisites

- Node.js 18+ and npm
- A New York Times API key (free tier available)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/kosterseb/newsify-app.git
   cd newsify-app
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**

   Create a `.env` file in the root directory:
   ```env
   VITE_NYT_API_KEY=your_api_key_here
   ```

   Get your free API key from [The New York Times Developer Portal](https://developer.nytimes.com/get-started)

4. **Start the development server**
   ```bash
   npm run dev
   ```

   The app will be available at `http://localhost:5173`

## Development

### Available Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server with hot reload |
| `npm run build` | Build production bundle to `dist/` |
| `npm run preview` | Preview production build locally |
| `npm run lint` | Run ESLint to check code quality |
| `npm test` | Run Vitest test suite |

### Project Structure

```
newsify-app/
├── .github/
│   └── workflows/
│       └── deploy.yml          # Automated deployment workflow
├── src/
│   ├── assets/                 # Images, icons, fonts
│   ├── components/             # React components
│   │   ├── Archive/           # Saved articles page
│   │   ├── Authentication/    # Auth/login screen
│   │   ├── BottomNav/         # Bottom navigation bar
│   │   ├── Home/              # Main news feed
│   │   ├── NewsCard/          # Reusable article card
│   │   ├── Onboarding/        # First-time user tutorial
│   │   ├── PageNotFound/      # 404 error page
│   │   ├── Popular/           # Popular news section
│   │   ├── Settings/          # User preferences
│   │   └── Splash/            # Splash screen
│   ├── contexts/              # React Context providers
│   │   ├── ArchiveContext.jsx # Archive state management
│   │   └── DarkModeContext.jsx # Theme state management
│   ├── hooks/                 # Custom React hooks
│   │   ├── usePullToRefresh.js # Pull-to-refresh logic
│   │   └── useSwipe.js        # Swipe gesture handling
│   ├── services/              # API services
│   │   └── newsApi.js         # NY Times API integration
│   ├── App.jsx                # Main app component & routing
│   └── main.jsx               # App entry point
├── .env.example               # Environment variables template
├── vite.config.js             # Vite configuration
└── package.json               # Project dependencies
```

## API Integration

The app uses The New York Times API to fetch news articles:

### Available Endpoints
- `getTopStories(section)` - Fetch top stories from a specific section
- `searchArticles(query)` - Search for articles by keyword

### API Rate Limits
- **500 requests per day** (free tier)
- **5 requests per minute**

The app implements smart caching to minimize API calls:
- Articles are stored in React state after fetching
- Pull-to-refresh manually triggers new API calls
- Category data persists in localStorage

## Deployment

The app is automatically deployed to GitHub Pages when changes are pushed to the `main` branch.

### Manual Deployment Steps

1. **Add NY Times API Key to GitHub Secrets**
   - Go to Settings → Secrets and variables → Actions
   - Create a new secret: `VITE_NYT_API_KEY`
   - Paste your API key as the value

2. **Configure GitHub Pages**
   - Go to Settings → Pages
   - Set Source to **GitHub Actions**

3. **Push to Main Branch**
   ```bash
   git checkout main
   git merge your-feature-branch
   git push origin main
   ```

4. **Monitor Deployment**
   - Go to the Actions tab on GitHub
   - Watch the "Deploy to GitHub Pages" workflow run
   - Once complete, your app is live!

### Local Build

To build the production bundle locally:

```bash
npm run build
```

The optimized files will be in the `dist/` directory.

## Features in Detail

### Swipe Gestures
- **Swipe Right** - Archive an article (shows green background)
- **Swipe Left** - Remove from archive (shows red background)

Implemented with a custom `useSwipe` hook that tracks touch events and calculates swipe distance.

### Dark Mode
Toggle between light and dark themes from the Settings page. Preference is saved to localStorage and applied across all components using Context API.

### Category Management
Enable or disable news categories in Settings. Only active categories appear in the Home and Popular feeds. Categories are stored in localStorage.

### Archive System
Save articles for later reading by swiping right. Archived articles are:
- Grouped by category
- Stored in localStorage
- Accessible from the Archive page
- Removable with left swipe

### Pull-to-Refresh
Pull down on the Home page to fetch fresh news. Visual feedback shows:
- Pull distance indicator
- Loading spinner during refresh
- Success message on complete

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Contributing

This is a student project for Roskilde Technical School (RTS). While not actively seeking contributions, feedback and suggestions are welcome!

## License

This project was created as part of the Web Developer program at Roskilde Tekniske Skole.

## Credits

- **Developer**: Sebastian Aguiar Køster
- **School**: Roskilde Tekniske Skole (RTS)
- **Program**: Webudvikler (WU14)
- **API**: [The New York Times Developer Network](https://developer.nytimes.com/)

## Links

- **Live App**: [https://kosterseb.github.io/newsify-app](https://kosterseb.github.io/newsify-app)
- **Repository**: [https://github.com/kosterseb/newsify-app](https://github.com/kosterseb/newsify-app)
- **Documentation**: See [projekt-dokumentation.md](./projekt-dokumentation.md) for detailed Danish documentation

---

Built with ❤️ using React + Vite
