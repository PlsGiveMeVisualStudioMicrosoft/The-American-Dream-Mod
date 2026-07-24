# The American Dream

**A modern-day North America overhaul for Hearts of Iron IV.**

🌐 **[theamericandreammod.site](https://theamericandreammod.site)** &nbsp;•&nbsp; 💬 **[Discord](https://discord.com/invite/GmhqdGmyEB)** &nbsp;•&nbsp; 🎮 Steam Workshop *(coming)*

This repository hosts the mod's public website; the roadmap page and the timeline planner. The mod itself is developed separately; everything here is the front end.

---

## About the mod

A North-America-only overhaul on a **2025 start date**, where all fifty states — alongside Mexico, the Caribbean and their neighbours — stand as their own playable countries.

- Full North American map, provinced and reworked from the ground up
- Real leaders and main opposition figures for every state
- Nationwide highway and supply network replacing the rail layer
- Resources, industry and research tuned per state
- Modernised tech trees running from 1991 to the present day
- Real 2025 military-industrial organisations

Dates on the roadmap are targets, not promises.

## Roadmap

| Version | Update | Status |
| --- | --- | --- |
| 0.1 | Foundation | 🟡 In progress |
| 0.2 | The New England Update | ⚪ Planned |
| 0.3 | The South American Update | 🟡 In progress |
| 0.4 | The 12 Colonies Update | ⚪ Planned |
| 1.0 | The Californian Dream | ⚪ Planned |

Full feature lists live on [the roadmap page](https://theamericandreammod.site).

---

## The website

### What's in this repo

| File | Purpose |
| --- | --- |
| `index.html` | The roadmap page. Self-contained — HTML, CSS, JS and the cover image are all in this one file. |
| `timeline.html` | The timeline planner, linked from the roadmap's legend. |
| `CNAME` | Tells GitHub Pages which custom domain to serve. **Don't edit or delete this** — see below. |

No build step, no dependencies, no framework. Push to `main` and the site updates in about a minute.

### Editing the roadmap

Open `index.html` and scroll to the block marked `EDIT HERE`. Everything you'd normally want to change lives in three constants:

- **`PAGE`** — the title, subtitle and intro paragraph at the top.
- **`COVER`** — the framed header image, embedded as a data URI. Set it to `""` to hide it, or swap in a file path like `"thumbnail.png"`.
- **`UPDATES`** — one object per version, rendered left to right along the rail.

Each update looks like this:

```js
{
  version: "0.3",
  name: "The South American Update",
  date: "In progress — Q1 2027",   // any text you like
  status: "progress",              // "released" | "progress" | "planned"
  image: "",                       // optional: "screenshots/map.png"
  features: [
    "Minor focus content for Mexico, Venezuela and Colombia",
    "Haiti expansion with a full civil-war path"
  ],
  note: "Optional free text under the features."
}
```

`status` controls the marker on the rail:

| Value | Marker |
| --- | --- |
| `released` | filled |
| `progress` | half-filled |
| `planned` | hollow |

To add a version, copy a whole `{ ... }` block and edit it. To remove one, delete the block.

### Previewing locally

Open `index.html` in a browser and you're done. If you'd rather serve it properly:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Hosting and DNS

The site is served by **GitHub Pages** from the `main` branch, `/ (root)`, on the custom domain `theamericandreammod.site`.

DNS records at the registrar:

| Type | Host | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `plsgivemevisualstudiomicrosoft.github.io.` |

The custom domain is set to the **bare apex** in Settings → Pages, not `www`. That matters: GitHub only issues a TLS certificate for the exact string in that field, and setting the apex gets you a certificate covering both the apex and `www`, with `www` redirecting automatically. Setting `www` there instead leaves the apex without a certificate.

The `CNAME` file in the repo root must match that setting. Pushing a `CNAME` with a different value — or deleting it — clears the custom domain and the site falls back to the `github.io` address until it's set again.

---

## Contributing

Bug reports, typos and suggestions are welcome — open an issue, or drop into the [Discord](https://discord.com/invite/GmhqdGmyEB), which is where most of the discussion happens.
