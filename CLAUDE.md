# Portfolio v3 — Claude Code Configuration

## Tech Stack
- **Framework**: Astro 4.16.18 (Static Site Generator)
- **Styling**: TailwindCSS 3.4.17
- **Icons**: Lucide Astro 0.469.0
- **Package Manager**: npm

## Core Libraries
- **astro** 4.16.18 — Static site generator dengan component islands
- **@astrojs/tailwind** 5.1.4 — TailwindCSS integration untuk Astro
- **tailwindcss** 3.4.17 — Utility-first CSS framework
- **lucide-astro** 0.469.0 — Icon library untuk Astro components

## Perintah Penting
```bash
npm run dev       # Development server
npm run build     # Build untuk production
npm run preview   # Preview production build
```

## Struktur Direktori
```
.
├── public/          # Static assets (favicon, resume.pdf, robots.txt)
├── src/
│   ├── components/  # Astro components untuk sections portfolio
│   ├── data/        # JSON data files (content portfolio)
│   ├── layouts/     # Layout utama (Layout.astro)
│   ├── pages/       # Routes (index.astro)
│   └── styles/      # Global CSS
```

## Module Map

### src/components/ — Portfolio sections & UI components
11 komponen Astro yang compose portfolio page:
- **About.astro** - Section "About Me"
- **Contact.astro** - Contact form/links
- **Education.astro** - Education timeline
- **Experience.astro** - Work experience timeline
- **Footer.astro** - Site footer
- **Hero.astro** - Landing hero section
- **Nav.astro** - Navigation bar
- **Projects.astro** - Project showcase grid
- **ResumeModal.astro** - Modal untuk download resume
- **Skills.astro** - Skills/tech stack display
- **ThemeToggle.astro** - Dark/light mode switcher

### src/data/ — Content JSON files
Data terpisah dari UI untuk maintainability:
- **site.json** - Site metadata (title, description, links)
- **education.json** - Education entries
- **experience.json** - Work experience entries
- **projects.json** - Project portfolio entries
- **skills.json** - Tech skills & categories

### src/layouts/ — Base layout
- **Layout.astro** - Root layout dengan HTML structure, meta tags, theme script

### src/pages/ — Routes
- **index.astro** - Homepage (compose semua components)

## Database Conventions
Tidak ada database — static site dengan JSON data.

## API Patterns
Tidak ada API layer — static site generation.

## Template & Layout
- **Base layout**: `src/layouts/Layout.astro`
  - Head: meta tags, title, favicon, theme script
  - Body: slot untuk page content
  - Dark mode: class-based (`class="dark"`)
- **Component composition**: `index.astro` import & render semua section components
- **Styling**: TailwindCSS utility classes + custom animations
- **Theme toggle**: Client-side script di ThemeToggle.astro, persist ke localStorage

## Base Classes & Utilities
Tidak ada base classes OOP — Astro menggunakan component composition.

**TailwindCSS custom config** (`tailwind.config.mjs`):
- **Custom colors**: `accent` palette (blue shades 50-950)
- **Custom animations**: `fade-up`, `fade-in`, `gradient`
- **Custom fonts**: Geist & Geist Mono
- **Dark mode**: class-based strategy

## Shared UI Components
Semua components di `src/components/` adalah reusable sections. Tidak ada nested shared components — architecture flat & simple.

## Integration Points
Entry points untuk extend portfolio:
- **Add new section**: buat component di `src/components/`, import & render di `src/pages/index.astro`
- **Update content**: edit JSON files di `src/data/`
- **Add new page**: buat `.astro` file di `src/pages/` (auto-routing)
- **Theme colors**: edit `tailwind.config.mjs` accent palette

## Auth & Session
Tidak ada auth — static site.

## Signals & Events
Tidak ada signals/events — static site generation.

## Release Config
- **release_remote**: belum dikonfigurasi — jalankan `/imp.release`
- **release_branch**: belum dikonfigurasi — jalankan `/imp.release`

## Workflow
Gunakan `/imp.dev <task>` untuk mengerjakan fitur. Workflow otomatis:
1. **Persiapan** — Cek branch, pull, jalankan test
2. **Analisis** — Cek Module Map, baca file terkait, analisis dampak
3. **Plan** — Masuk plan mode, buat implementation plan, tunggu approval user
4. **Eksekusi** — Implementasi sesuai plan yang disetujui
5. **Quality Check** — Code review + refactor
6. **Verifikasi** — Test, commit, ringkasan

## Aturan Umum (WAJIB diikuti setiap saat)

### Reuse First
- Sebelum menulis kode baru, **cek Module Map dan Shared UI Components** di atas
- **DILARANG membuat komponen UI baru jika sudah ada yang serupa** — gunakan yang existing
- Untuk add section baru: cek pattern di components existing, ikuti structure yang sama
- Data changes: edit JSON di `src/data/`, jangan hardcode di components

### Plan Before Code (WAJIB — tanpa pengecualian)
- **DILARANG KERAS menulis/mengedit kode implementasi SEBELUM user menyetujui plan**
- **SEMUA perubahan kode WAJIB masuk `EnterPlanMode`** — sekecil apapun perubahannya, termasuk fix 1 file
- Alur WAJIB: analisis → `EnterPlanMode` → tulis plan → tunggu user approve via `ExitPlanMode` → baru implementasi
- Ini berlaku untuk SEMUA prompt: `/imp.*` commands, prompt ad-hoc, maupun instruksi langsung dari user
- **Satu-satunya pengecualian**: prompt yang TIDAK mengubah kode (pertanyaan, review, analisis read-only)

### Development Log (WAJIB — setiap prompt yang mengubah kode)
**PENTING: Aturan ini berlaku untuk SEMUA prompt — termasuk prompt ad-hoc di luar command `/imp.*`.**
Setiap kali selesai mengerjakan prompt yang mengubah kode, WAJIB:
1. Load skill `sop-devlog`
2. Update file `docs/devlogs/<YYYYMMDD>-<nama_branch>.md`
3. Commit devlog bersama kode perubahan

Skip HANYA untuk: fix typo, rename variabel, formatting saja.

### Update CLAUDE.md (WAJIB — setiap prompt yang mengubah kode)
**PENTING: Aturan ini berlaku untuk SEMUA prompt — termasuk prompt ad-hoc di luar command `/imp.*`.**
Setiap kali selesai mengerjakan prompt yang mengubah kode, cek apakah CLAUDE.md perlu di-update.
Update secara incremental (via `Edit`, JANGAN full regenerate):

- Component baru di `src/components/` → update **Module Map** section `src/components/`
- Data file baru di `src/data/` → update **Module Map** section `src/data/`
- Page baru di `src/pages/` → update **Module Map** section `src/pages/`
- Dependency baru di-install (npm install) → update **Tech Stack** dan **Core Libraries**
- Folder/struktur baru dibuat → update **Struktur Direktori**
- TailwindCSS config berubah (colors, animations, plugins) → update **Base Classes & Utilities**
- Integration point baru (cara add feature, routing pattern berubah) → update **Integration Points**
- Build/dev commands berubah → update **Perintah Penting**

Skip HANYA untuk: bug fix tanpa ubah struktur, fix typo, rename variabel, formatting.

### Aturan Kode
Lihat skill `coding-standards` untuk aturan lengkap. Highlights:
- Maksimal 88 karakter per baris, 30 baris per function, 400 baris per file
- Type hints WAJIB di TypeScript, docstring WAJIB di public function
- Conventional commits, 1 task = 1 commit
- **DILARANG** menambahkan `Co-Authored-By` pada semua commit — tanpa pengecualian
- Bahasa Indonesia untuk komunikasi, English untuk kode

## Agent & Skill yang Tersedia

### Agents
Tidak ada custom agents.

### Skills
Tidak ada custom skills.

### Commands
Tidak ada custom commands.
