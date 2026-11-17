# 3nime — Premium Anime News Website

A complete, static anime news publication built with **pure HTML5 + CSS3**.
No frameworks, no JavaScript, no build step. The design follows a Japanese
editorial-magazine aesthetic: warm off-white paper, deep charcoal ink,
vermilion accents, mincho-style display serif and clean gothic body type.

---

## 1. Download & Extract the ZIP

1. Download `3nime-website.zip`.
2. Right-click the file and choose **Extract All** (Windows) /
   double-click it (macOS) / run `unzip 3nime-website.zip` (Linux).
3. You get a folder called `3nime/` containing the whole project.

## 2. Open the Project in Visual Studio Code

1. Install VS Code: https://code.visualstudio.com
2. Go to **File → Open Folder…** and select the `3nime/` folder.
3. Recommended extension: **Live Server** (by Ritwick Dey) — it gives you
   hot reload while you edit.

## 3. Run the Website Locally

Pick whichever is easiest:

| Method | Steps |
| --- | --- |
| **Simplest** | Double-click `index.html` — it opens in your browser. |
| **VS Code Live Server** | Right-click `index.html` → **Open with Live Server**. |
| **Python** | In the project folder run `python3 -m http.server 8000`, then open `http://localhost:8000`. |
| **Node** | Run `npx serve .`, then open the printed URL. |

> The site works fully offline except for Google Fonts (it falls back to
> system fonts when offline).

## 4. Modify News Articles & Images

All content lives in **`index.html`** — it is plain, commented HTML.

**Edit an article**
- Hero story: inside `<section class="hero">`.
- News grid: inside `<section id="latest-news">` — each card is an
  `<article>` (`card--feature`, `card--row`, `card--std`, `card--text`,
  `card--wide`, `card--tall`).
- Trending list: inside `<section id="trending">` (`trend-row` items).
- Upcoming releases: inside `<section id="upcoming">` (`up-card` items).
- Spotlight feature: inside `<section id="spotlight">`.

Change the headline text, the `<p class="card-desc">` excerpt, the
`<time datetime="…">` date and the category in `<span class="tag">`.
Update `width` / `height` attributes when you swap an image so the layout
stays correct.

**Replace an image**
1. Drop your file into `assets/img/` (JPG, ideally ≤ 1600 px wide,
   ~80% quality).
2. Point the matching `<img src="assets/img/your-file.jpg">` at it.
3. Update the `alt` text and the `width`/`height` attributes.

**Image aspect ratios used by the layout**
- Hero image: 16 : 10
- Feature card: 16 : 10 · standard cards: 16 : 9
- Compact "row" thumbs: 4 : 3
- Portrait card & posters: 4 : 5 and 2 : 3
- Spotlight: 16 : 10

## 5. Customize Colors, Fonts & Branding

**Colors** — open `style.css`; every color is a CSS variable in
`:root` (section *01. DESIGN TOKENS*):

```css
--bg:         #F7F6F2;  /* page background        */
--bg-soft:    #ECEBE7;  /* soft gray surfaces     */
--ink:        #171717;  /* main text & dark areas */
--muted:      #777777;  /* secondary text         */
--red:        #E63935;  /* vermilion accent       */
--red-deep:   #C22B28;  /* hover red              */
--red-bright: #FF6E69;  /* red for dark surfaces  */
```

Change these once and the whole site follows.

**Fonts** — the two families are loaded from Google Fonts in `index.html`
(`<link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho+B1…&family=Zen+Kaku+Gothic+New…">`)
and assigned in `style.css`:

```css
--font-display: "Shippori Mincho B1", …;  /* headlines, numbers */
--font-body:    "Zen Kaku Gothic New", …; /* everything else    */
```

Swap the family names (both here and in the `<link>` tag) to rebrand the
typography. Keep it to two families to preserve the editorial look.

**Branding**
- Wordmark: `<a class="brand">` in the header and footer — the red square
  is `.brand-mark`, the word is `.brand-word`.
- Favicon: inline SVG in `index.html` `<link rel="icon">` (change the
  `%23E63935` fill and the letter).
- Site title / description: the `<title>` and `<meta name="description">`
  tags at the top of `index.html`.

## Project Structure

```
3nime/
├── index.html          ← all content & structure
├── style.css           ← design system & all styling (commented)
├── README.md
└── assets/
    └── img/            ← 14 optimized images (~2.4 MB total)
```

## Design Notes

- **Grid**: 12-column CSS Grid for the news section; Flexbox for nav,
  meta rows and lists.
- **Breakpoints**: 1100 px, 960 px, 880 px (mobile nav), 680 px
  (posters become a swipeable rail), 580 px.
- **No JavaScript**: the mobile menu and the search drawer run on the
  CSS checkbox technique; hover states handle the rest.
- **Accessibility**: skip link, semantic landmarks, meaningful alt text,
  visible `:focus-visible` outlines, `prefers-reduced-motion` support.

Images are publicly sourced promotional artwork used here for
demonstration purposes; all titles and trademarks belong to their
respective studios. Replace them with licensed assets before any
production use.
