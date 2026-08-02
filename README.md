# Portfolio V3

A modern, performant portfolio website built with Astro, showcasing professional experience, projects, and skills. Features a dark-mode-first design with smooth animations and a content-driven architecture.

## ✨ Features

- **Fast & Lightweight** - Built with Astro for optimal performance and minimal JavaScript
- **Dark Mode** - System-aware theme with manual toggle support
- **Responsive Design** - Mobile-first approach that works seamlessly across all devices
- **Content-Driven** - Easy content management through JSON data files
- **Modern UI** - Clean, professional design with smooth animations
- **SEO Optimized** - Static site generation for excellent search engine visibility
- **Accessible** - Built with accessibility best practices

## 🛠️ Tech Stack

- **[Astro](https://astro.build/)** - Static site framework
- **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **[Lucide Icons](https://lucide.dev/)** - Beautiful, consistent icon set
- **TypeScript** - Type-safe development

## 📁 Project Structure

```
portfolio-v3/
├── src/
│   ├── components/          # Reusable Astro components
│   │   ├── About.astro
│   │   ├── Contact.astro
│   │   ├── Education.astro
│   │   ├── Experience.astro
│   │   ├── Footer.astro
│   │   ├── Hero.astro
│   │   ├── Nav.astro
│   │   ├── Projects.astro
│   │   ├── ResumeModal.astro
│   │   ├── Skills.astro
│   │   └── ThemeToggle.astro
│   ├── data/                # Content data files (JSON)
│   │   ├── education.json
│   │   ├── experience.json
│   │   ├── projects.json
│   │   ├── site.json
│   │   └── skills.json
│   ├── layouts/             # Page layouts
│   │   └── Layout.astro
│   ├── pages/               # Routes
│   │   └── index.astro
│   ├── styles/              # Global styles
│   └── env.d.ts
├── public/                  # Static assets
├── astro.config.mjs         # Astro configuration
├── tailwind.config.mjs      # Tailwind configuration
└── package.json
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ installed
- npm or yarn package manager

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd portfolio-v3
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open [http://localhost:4321](http://localhost:4321) in your browser

## 📝 Development

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
- `npm start` - Alias for `npm run dev`

### Updating Content

All content is managed through JSON files in the `src/data/` directory. Simply edit these files to update your portfolio:

#### `src/data/site.json`
General site information like name, title, bio, and social links.

#### `src/data/experience.json`
Work experience entries with company, role, dates, and descriptions.

```json
{
  "experience": [
    {
      "company": "Company Name",
      "role": "Your Role",
      "startDate": "Jan 2023",
      "endDate": "Present",
      "description": "What you did...",
      "technologies": ["Tech1", "Tech2"]
    }
  ]
}
```

#### `src/data/projects.json`
Project showcase with titles, descriptions, technologies, and links.

```json
{
  "projects": [
    {
      "title": "Project Name",
      "description": "Project description...",
      "technologies": ["React", "Node.js"],
      "link": "https://example.com",
      "github": "https://github.com/username/repo"
    }
  ]
}
```

#### `src/data/skills.json`
Technical skills organized by categories.

```json
{
  "categories": [
    {
      "name": "Frontend",
      "skills": ["React", "TypeScript", "Tailwind CSS"]
    }
  ]
}
```

#### `src/data/education.json`
Educational background with institutions, degrees, and dates.

### Customizing Styles

- Tailwind configuration: `tailwind.config.mjs`
- Global styles: `src/styles/`
- Component-specific styles: Scoped `<style>` tags in `.astro` files

## 🏗️ Building for Production

Build the static site:

```bash
npm run build
```

The output will be in the `dist/` directory, ready to deploy to any static hosting service.

Preview the production build locally:

```bash
npm run preview
```

## 🚢 Deployment

This site can be deployed to any static hosting platform:

### Netlify

1. Connect your repository to Netlify
2. Set build command: `npm run build`
3. Set publish directory: `dist`
4. Deploy!

### Vercel

1. Import your repository to Vercel
2. Framework preset: Astro
3. Deploy!

### Other Platforms

The `dist/` folder contains a complete static site that can be served from:
- GitHub Pages
- Cloudflare Pages
- AWS S3 + CloudFront
- Any static hosting service

## 🎨 Design Philosophy

This portfolio follows a "Dark Tech Minimal" aesthetic:

- Dark mode as default with light mode support
- Clean, professional typography
- Smooth scroll-triggered animations
- Glassmorphism cards with subtle effects
- Mobile-first responsive design
- Minimal JavaScript footprint

## 📄 License

This project is private and not open source.

## 👤 Author

**Muhammad Farras Jibran**

- Email: farasjibran@gmail.com
- Portfolio: [farras-jibran.netlify.app](https://farras-jibran.netlify.app)
- GitHub: [@your-github-username](https://github.com/your-github-username)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/your-profile)

---

Built with [Astro](https://astro.build/) 🚀
