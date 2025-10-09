# Editing & Maintenance Guide

This site uses **Just the Docs** on GitHub Pages (no local Ruby needed).  
Everything builds automatically when you **commit & push** to `main`.

---

## 🧭 Quick workflow

1. Open the folder in VS Code.  
2. Make your edits (add pages, change colors, etc.).  
3. Commit & push:
   ```bash
   git add -A
   git commit -m "docs: explain X / add Y"
   git push
Wait ±1 minute → the site auto-updates.

📁 Repository structure
pgsql
Copy code
_config.yml
index.md
methods/
  index.md
  methodiek-template.md
_sass/
  color_schemes/
    brown.scss
README.md
LICENSE
➕ Add a new top-level section (e.g., “Introduction”)
Create a new folder with an index.md:

pgsql
Copy code
introduction/
  index.md
Add this front matter to the file:

markdown
Copy code
---
title: Introduction
nav_order: 2
has_children: true
---

# Introduction

Welcome text…
Adjust nav_order numbers in each section to control sidebar order
(1 = top, 2 = next, etc.).

📄 Add a page inside a section
Example: new page under Methods.

Create methods/collecting-edna.md:

markdown
Copy code
---
title: Collecting eDNA
parent: Methods
nav_order: 10
---

# Collecting eDNA

Content here…
parent: must match the section’s title in its index.md.

🗂 Add another folder next to methods
Example: create a Cases section.

pgsql
Copy code
cases/
  index.md
markdown
Copy code
---
title: Cases
nav_order: 3
has_children: true
---

# Cases

Describe what lives here…
Then add pages in cases/ with parent: Cases.

🖼 Add images & files
Store images in assets/images/

markdown
Copy code
![Alt text](/assets/images/edna-kit.jpg)
PDFs or other downloads → assets/files/

markdown
Copy code
[Download the checklist](/assets/files/checklist.pdf)
🧭 Navigation & links
Relative internal link:

markdown
Copy code
See [Methods](../methods/index.md)
External links in header via _config.yml:

yaml
Copy code
aux_links:
  "Citizen Science Lab":
    - "https://www.universiteitleiden.nl/en/citizen-science-lab"
🎨 Styling & color customization
Color scheme (already active)
File: _sass/color_schemes/brown.scss

Config: _config.yml contains

yaml
Copy code
color_scheme: brown
Change variables in brown.scss, e.g.:

scss
Copy code
$link-color: #8b5e3c;
$link-hover-color: darken($link-color, 10%);
$btn-primary-color: #8b5e3c;
$sidebar-color: #f8f6f4;
$border-color: #d8c9b3;
Add extra CSS overrides
Create assets/css/just-the-docs.scss:

scss
Copy code
---
---

@import "just-the-docs";

/* Custom tweaks */
.page-title {
  letter-spacing: 0.2px;
}
Push → Pages rebuilds automatically.

🧾 Front matter cheat-sheet
yaml
Copy code
---
title: Page Title
nav_order: 5
parent: Methods
grand_parent: ...
has_children: true
permalink: /intro/
---
🔍 Search
Enabled by default via _config.yml:

yaml
Copy code
search_enabled: true
No extra setup needed.

🏠 Edit home page
index.md controls the front page:

markdown
Copy code
---
title: Home
nav_order: 1
---

# Leiden BuurtKennis

Intro text…
🧰 Common fixes
Problem	Check
Page not showing	Missing --- block or wrong parent:
Styles not updating	Ensure SCSS file starts with --- front matter
Build not updating	Push a small change to retrigger; check Deployments → github-pages logs

🌿 Optional branch workflow (safe edits)
bash
Copy code
git checkout -b docs/new-section
# edit files…
git add -A
git commit -m "docs: add Introduction section"
git push -u origin docs/new-section
Open a Pull Request, review, merge to main.

⚖️ License notice
Add this footer line where relevant:

markdown
Copy code
*Unless noted otherwise, content is licensed under **CC BY 4.0**.*
⚙️ Global settings reference (_config.yml)
yaml
Copy code
title: "Leiden-BuurtKennis"
description: "Public documentation of citizen science methods from Leiden Citizen Science Lab"
url: https://citizensciencelab.github.io/Leiden-BuurtKennis
remote_theme: just-the-docs/just-the-docs
plugins:
  - jekyll-remote-theme
search_enabled: true
color_scheme: brown
aux_links:
  "Citizen Science Lab":
    - "https://www.universiteitleiden.nl/en/citizen-science-lab"
🧩 In short:
Edit Markdown → commit → push → watch GitHub Pages rebuild automatically.
No local Ruby setup required.

yaml
Copy code

---

✅ **Save as:** `EDITING.md`  
✅ **Location:** root of your repo  
Once committed, contributors (including future you) will have a simple, always-up-to-date guide for editing your site.




