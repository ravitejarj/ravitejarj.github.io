# Raviteja Kalavena — Portfolio

A clean, split‑section portfolio website built from simple HTML/CSS/JS.  
Each section lives in `/sections/*.html` and is dynamically loaded into `index.html` with `fetch()` for fast editing and reuse.

---

## ✨ Features
- **Split sections**: Update a section without touching the rest of the page.
- **Lightweight**: No frameworks; just HTML/CSS/JS.
- **Mobile friendly**: Responsive layout and media queries.
- **Easy content swaps**: Resume file, social links, and images are in `/assets`.
- **Timeline & skills**: Clean work‑experience timeline and two‑column skill cards.

---

## 📁 Folder Structure
```
index.html
style.css
mediaqueries.css
script.js
assets/
  profile_pic.png
  about-pic.jpg
  experience.png
  education.png
  linkedin.png
  github.png
  checkmark.png
  project-1.png
  project-2.png
  project-3.png
  arrow.png
  email.png
  raviteja_resume.pdf
sections/
  header.html
  profile.html
  about.html
  skills.html
  experience.html
  projects.html
  contact.html
  footer.html
```

---

## 🚀 Getting Started

### 1) Clone / Download
```bash
git clone https://github.com/<your-username>/<your-portfolio-repo>.git
cd <your-portfolio-repo>
```

### 2) Run a Local Server
Because sections are loaded with `fetch()`, **file://** won’t work. Use any of the following:

- **VS Code**: Install *Live Server* → right‑click `index.html` → *Open with Live Server*
- **Python**:
  ```bash
  python -m http.server 5500
  # open http://localhost:5500
  ```
- **Node**:
  ```bash
  npx http-server -p 5500
  # open http://localhost:5500
  ```

---

## 🧩 How Sections Load
`index.html` contains placeholders and a tiny loader:

```html
<div id="header"></div>
<div id="profile"></div>
<div id="about"></div>
<div id="skills"></div>
<div id="experience"></div>
<div id="projects"></div>
<div id="contact"></div>
<div id="footer"></div>

<script>
  const sections = ["header","profile","about","skills","experience","projects","contact","footer"];
  sections.forEach(async (name) => {
    try {
      const res = await fetch(\`sections/\${name}.html\`, { cache: "no-cache" });
      if (!res.ok) throw new Error(\`\${name}.html \${res.status}\`);
      document.getElementById(name).innerHTML = await res.text();
    } catch (e) { console.error(e); }
  });
</script>
```

To add a new section:
1. Create `sections/<name>.html`
2. Add `<div id="<name>"></div>` to `index.html`
3. Add `"<name>"` to the `sections` array above.

---

## 🖼️ Customizing Content

- **Profile**: Edit `sections/profile.html` — name, role, phone/email line, social links, and CTA buttons.
- **About**: `sections/about.html` — summary and education format.
- **Experience**: `sections/experience.html` — timeline items.  
  - To remove the center icon boxes, delete each `<div class="timeline-icon">…</div>` (or hide via CSS).
- **Skills**: `sections/skills.html` — two categories; items are simple `<article>` rows.
- **Projects**: `sections/projects.html` — cards with image + link.
- **Contact**: `sections/contact.html` — email and LinkedIn.
- **Resume**: Replace `/assets/raviteja_resume.pdf` and keep the same filename (or update the button path).

---

## 🎨 Styling
- Global styles in `style.css`, responsive tweaks in `mediaqueries.css`.
- Buttons use the **sharp** style (square‑ish corners): change `.btn` in `style.css` to adjust sizing.
- Experience timeline CSS lives at the bottom of `style.css` under:
  ```css
  /* ---- Work Experience Timeline (clean, reliable) ---- */
  ```
- Skills alignment: look for the `#skills` rules near the bottom to tweak spacing and grids.

---

## 📦 Deployment

### GitHub Pages
1. Push the repo to `main` (or `master`).
2. In **Settings → Pages**, set Source to **Deploy from a branch** and choose `main`/`root`.
3. Wait for the green check, then open the Pages URL.

### Netlify (recommended for quick deploys)
- Drag‑and‑drop the folder on https://app.netlify.com/ or connect your GitHub repo.
- Build settings: **No build command**, **Publish directory**: `/` (project root).

---

## 🧰 Troubleshooting
- **Sections don’t load**: You’re probably opening `index.html` via `file://`. Use a local server.
- **Broken images**: Check paths like `./assets/<name>.png` from the file that’s referencing them.
- **Resume button not working**: Ensure the file is named exactly `raviteja_resume.pdf` in `/assets` or update the path in `profile.html`.

---

## 🧑‍💻 Author
**Raviteja Kalavena** — Machine Learning & Python Developer  
Atlanta, GA • +1 (334) 354‑5864 • ravitejarj25@gmail.com  
LinkedIn: https://www.linkedin.com/in/raviteja-kalavena-548645158/  
GitHub: https://github.com/ravitejarj

---

## 📝 License
This project is open‑sourced under the MIT License. Feel free to use and adapt.
