# Second Circuit — E-Waste Segregation & Certified Recycler Directory

A concept website built from the technical report *"Improper Disposal of
Electronic Waste."* It has two parts:

1. **An educational segregation guide** — helps a visitor identify which
   category their device falls into and why it needs careful handling.
2. **A searchable, filterable directory of certified recyclers** — by
   state/city and by the type of e-waste accepted.

Two versions of the site are provided. They look and behave identically —
pick whichever fits how you want to use or host it.

---

## 1. Single-page version — `ewaste-directory.html`

Everything (HTML, CSS, JavaScript) lives in **one file**. There is nothing
else to download or keep alongside it.

**To use it:** double-click the file, or drag it into a browser window
(Chrome, Firefox, Edge, Safari all work). No server, no build step, no
internet connection required except to load the two Google Fonts.

This is the simplest option if you just want to open it locally, email it
to someone, or drop it into any basic web host as-is.

---

## 2. Four-page version — `second-circuit-site/` folder

The same content, split into four linked pages with a shared navigation
bar and footer:

| File            | Page                                      |
|------------------|-------------------------------------------|
| `index.html`     | Home — intro, key stats, links to the rest |
| `guide.html`     | Segregation guide                          |
| `directory.html` | Recycler directory (search + filters)      |
| `about.html`     | About the project, SDGs, ISO 14001, FAQ    |

Each page is **also fully self-contained** (its own inline `<style>` and
`<script>`) — there are no shared `.css` or `.js` files to lose track of.
You can open any single page on its own and it will work.

**To use it:**
- Unzip `second-circuit-site.zip`.
- Keep all four `.html` files in the **same folder** (the navigation links
  between them use relative paths like `guide.html`).
- Open `index.html` in a browser to start browsing from the home page.

This version is better if you want an actual multi-page site to host
(e.g. on GitHub Pages, Netlify, or a college project server).

---

## What's interactive

- **Segregation guide:** click a category tile to expand hazard info and a
  handling tip for that type of device.
- **Recycler directory:** type in the search box, or pick a state / e-waste
  type from the dropdowns — the list filters live as you type (case
  insensitive), and shows a "no recyclers match" message when nothing
  fits.
- **FAQ (about page):** click a question to expand its answer.

---

## Important: the recycler data is a placeholder

The 10 recycler listings are **illustrative sample data**, not verified
real businesses. Before using this for anything real, replace the
`recyclers` array (near the top of each page's `<script>` block) with
actual authorised-recycler records pulled from your State Pollution
Control Board or the Central Pollution Control Board's published list —
this is exactly what the report's feasibility section describes doing.

Each entry follows this shape:

```js
{
  name: "Recycler Name",
  city: "City",
  state: "State",
  types: ["it", "small", "battery", "large", "lighting"], // pick any that apply
  auth: "Authorisation note, e.g. 'SPCB Kerala authorised dismantler'"
}
```

## Customizing

- **Colors / fonts:** defined as CSS custom properties (`--forest`,
  `--copper`, etc.) near the top of each `<style>` block — change them
  once and the whole page updates.
- **Categories, FAQ entries:** edit the `categories` / `faqs` arrays in
  the `<script>` block the same way as the recycler data above.
- **Adding a real backend:** the report's tech stack suggestion (Node.js
  + Express or PHP, with MySQL/SQLite) would replace the hardcoded
  `recyclers` array with an API call — the front-end filtering logic
  would stay the same.
