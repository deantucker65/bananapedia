# Bananapedia — How to Add Content

A quick cheat-sheet for adding articles and sections. Pushing to GitHub
auto-deploys to Cloudflare, so publishing is just a `git push`.

## Add a new article

1. Create a `.md` file in `src/content/articles/` (name it anything, e.g. `banana-smoothies.md`).
2. Start it with this frontmatter block, then write Markdown below it:

   ```markdown
   ---
   title: "Five Banana Smoothies Worth Blending"
   section: recipes
   description: Quick, creamy, and impossible to mess up.
   order: 2
   ---

   ## Classic Banana-Berry

   Your content here. Use **bold**, *italics*, lists, > quotes, ## headings, etc.
   ```

- **section** must match a section `slug` from `src/lib/sections.js` (e.g. `recipes`, `history`, `jokes`).
- **order** sorts articles on the section page (lower number = higher up).
- **description** is the subtitle shown in the article list.

No config to touch. The article appears on its section page and gets a URL like `/recipes/banana-smoothies`.

## Add a new section

Edit `src/lib/sections.js` and add one line to the array:

```js
{ slug: 'farming', name: 'Farming', emoji: '🚜', tagline: 'How bananas actually get grown and shipped.' },
```

- **slug** = the URL + the value articles put in their `section:` field (lowercase, no spaces).
- **name** = the label in the nav and homepage tile.
- **emoji** + **tagline** = the icon and one-liner on the homepage card.

Then add at least one article with `section: farming` so it isn't empty.
(No need to edit `content.config.ts` — the section field accepts any string.)

## Preview locally (optional)

```
npm run dev
```

Open the localhost URL it prints. What you see there is what will publish.

## Publish

```
git add .
git commit -m "Add banana smoothies article"
git push
```

The push triggers Cloudflare to rebuild and redeploy — live in a minute or two.

## Live URLs

- Custom domain: https://bananapedia.org
- Cloudflare worker URL: https://bananapedia-site.bananapedia.workers.dev
