# KJV Bible Study Guide

A static, GitHub Pages-compatible personal Bible study site.

## How to Deploy

1. Push this entire folder to a GitHub repository.
2. Go to **Settings → Pages** → set Source to `main` branch, root `/`.
3. Your site will be live at `https://yourusername.github.io/your-repo/`.

---

## File Structure

```
index.html              ← The entire app (single file)
data/
  index.json            ← Manifest — lists all books & chapters  ← YOU MAINTAIN THIS
  genesis/
    overview.md         ← Book introduction page
    1/
      guide.md          ← Chapter 1 study guide
    2/
      guide.md          ← Chapter 2 study guide
  john/
    overview.md
    1/
      guide.md
```

---

## Adding a New Book

### 1. Create the folder and files

```
data/
  romans/
    overview.md
    1/
      guide.md
```

### 2. Register it in `data/index.json`

```json
{
  "books": [
    {
      "id": "romans",
      "name": "Romans",
      "testament": "NT",
      "chapters": [
        { "id": "1", "title": "Chapter 1 — The Gospel of God" },
        { "id": "2", "title": "Chapter 2 — God's Righteous Judgment" }
      ]
    }
  ]
}
```

- **`id`** must match the folder name exactly (lowercase, no spaces).
- **`testament`** is optional (`"OT"` or `"NT"`). When present, the sidebar splits into Old / New Testament sections.
- **`chapters`** is an array of objects. Add each chapter after you write its guide.

---

## Writing Content

### `overview.md` — Book Introduction

Use standard Markdown. Suggested sections:

```markdown
# Book Name

## Overview
Brief description of the book.

## Key Themes
- Theme 1
- Theme 2

## Key Verse
> "Verse text here." — Reference

## Structure
| Section | Chapters | Focus |
|---------|----------|-------|
| ... | ... | ... |
```

### `guide.md` — Chapter Study Guide

```markdown
# Book Chapter — Title

## Key Verses
> "Verse..." — Reference

## Context
Background and setting.

## Study Notes
### Sub-topic
Content...

## Discussion Questions
1. Question one?
2. Question two?

## Cross References
- **Reference** — brief note
```

---

## Search

The search bar (or **Ctrl/Cmd + K**) searches all registered books and chapter titles from `index.json`. It does not search file content — only titles.

---

## Notes

- No build step required. Everything runs in the browser.
- Markdown is rendered client-side via [marked.js](https://marked.js.org/).
- The site fetches files with `fetch()` — this works on GitHub Pages but **not** from a local `file://` path. Use a local server (e.g., `python3 -m http.server`) for local testing.
