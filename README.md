# AtoZ Service Hub

A complete, responsive static website for a service directory covering jobs, government schemes, free courses, daily updates, and service providers.

## 🚀 Live Demo

Deploy to GitHub Pages — see setup below.

## 📁 Project Structure

```
atozhub/
├── index.html              # Homepage
├── css/
│   └── style.css           # All styles (design system)
├── js/
│   └── main.js             # Navigation, filtering, search logic
└── pages/
    ├── latest-jobs.html    # Job listings with category filter
    ├── govt-schemes.html   # Government schemes directory
    ├── free-courses.html   # Free online courses
    ├── daily-updates.html  # Exam alerts, results, news
    ├── service-providers.html  # Local service directory
    ├── contact.html        # Contact form
    ├── about.html          # About page
    ├── privacy.html        # Privacy policy
    └── terms.html          # Terms of service
```

## ✅ Features

- **Fully static** — no backend required, deploys anywhere
- **Responsive** — works on mobile, tablet, and desktop
- **Search & Filter** — client-side filtering on all listing pages
- **Dark theme** — elegant dark UI with gold/teal accents
- **Smooth animations** — fade-up on scroll, hover states
- **All pages complete** — no broken links, no "No posts found" errors
- **SEO ready** — meta titles and descriptions on every page

## 🌐 Deploy to GitHub Pages

1. Push this repository to GitHub
2. Go to **Settings → Pages**
3. Set **Source** to `main` branch, `/ (root)` folder
4. Click **Save** — your site will be live at `https://yourusername.github.io/repository-name/`

## 🖥️ Run Locally

No build step needed! Simply open `index.html` in your browser, or use a simple server:

```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```

## 🔧 Customization

- Edit content directly in the HTML files
- Colors and fonts are controlled via CSS variables in `css/style.css`
- Add new posts by duplicating `.post-card` or `.feature-card` blocks

## 📄 License

MIT — free to use and modify.
