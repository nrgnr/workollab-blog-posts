# Workollab Blog Posts

Push Markdown files here and they will be published automatically to `https://blogs.workollab.com/`.

## How it works

- Add a `.md` file to the repo
- Commit and push to `main`
- The publisher checks every 10 minutes
- New or updated Markdown files become Ghost posts

## What is supported

- Markdown headings, paragraphs, lists, links, quotes, code blocks, and tables
- Frontmatter fields like `title`, `slug`, `tags`, and `excerpt`
- External images using normal Markdown image syntax
- Embedded HTML when Ghost accepts it, for example YouTube/Vimeo iframe embeds

## What is not automated yet

- Uploading local image files from the repo into Ghost
- Uploading video files into Ghost
- Managing Ghost image galleries or richer editor cards from Markdown

So today, if you want pictures or video inside a repo-driven post:

- Use public image URLs:
  - `![Alt text](https://example.com/image.jpg)`
- Use public video embeds:
  - paste a supported embed iframe into the Markdown file

If you put image or video files directly in this repo, they will not be uploaded to Ghost automatically yet.

## Recommended structure

- Keep one post per file
- Use frontmatter for title, slug, tags, and excerpt
- Store reusable structure in `templates/post-template.md`
- Do not expect `README.md` or files inside `templates/` to publish

## Example frontmatter

```md
---
title: Your post title here
slug: your-post-slug-here
tags:
  - Blog Posts
  - Work Updates
excerpt: One short summary sentence for cards and previews.
---
```
