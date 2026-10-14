# anabsilva.com

Personal website of Ana Beatriz Silva — Strategy & Analytics professional based in Ireland.

🌐 **[www.anabsilva.com](https://www.anabsilva.com/)**

## About the site

A minimal, fast personal site built to showcase Ana's work and background as a data analyst with experience across financial services, operations, risk, and BI. No frameworks, no build step — just HTML, CSS, and a small amount of vanilla JavaScript.

## Tech stack

- **Stack**: plain HTML, CSS, and JavaScript. No dependencies, no build step.
- **Fonts**: Cormorant Garamond + DM Sans, loaded from Google Fonts.
- **Hosting**: Vercel (`vercel.json` holds the security headers and cache rules).

## Structure

```
index.html              Home — hero, about, expertise, certifications,
                        volunteering, connect
                        (all CSS is inline in the <style> block)
portfolio/
  index.html            Project list
  portfolio.css
blog/
  index.html            Post list
  blog.css              Shared by the list and the posts
  post-template.html    Copy this per post, fill in the {{PLACEHOLDERS}}
  feed.xml              Atom feed, maintained by hand
assets/
  images/               profile.jpg, og-default.jpg (link preview card)
  img/favicons/         Favicon set — SVG, PNG at every standard size
```

## Pages

| Page | Path | What's on it |
|---|---|---|
| Home | `/` | Hero, About, Expertise, Certifications & Education, Volunteering, Connect |
| Portfolio | `/portfolio/` | Project cards — add one per project |
| Blog | `/blog/` | Post list + Atom feed |

## How to edit

### Update the About or Hero copy

Everything is in `index.html`. The CSS tokens (colours, fonts, spacing) are in the `:root` block at the top of the `<style>` tag. The colour palette is a soft blush pink — `--bg: #FEF0EE`, `--bg-alt: #FADDD8`, accent `--accent: #9E3F55`.

### Add a certification or education entry

Open `index.html` and find the `<!-- ── CERTIFICATIONS -->` section. Copy an existing `.cert-item` block and update the name, issuer, date, and status class (`is-earned` or `is-progress`).

### Add a volunteering entry

Find the `<!-- ── VOLUNTEERING -->` section in `index.html`. Same structure as certifications — copy a `.cert-item` and fill in the details.

### Add a project

Open `portfolio/index.html` and follow the `✏️` comment: uncomment the project grid and copy one `.project-card` per project. Newest goes on top.

### Publish a blog post

1. Copy `blog/post-template.html` to `blog/your-slug.html`.
2. Replace every `{{PLACEHOLDER}}` (the list is in a comment at the top of the file).
3. Add a `.blog-post-item` to `blog/index.html` and delete the `.blog-empty` block.
4. Add an `<entry>` to `blog/feed.xml` and bump its `<updated>` date.
5. Add the URL to `sitemap.xml`.

## Things to keep in mind

- **Colours live in one place per file.** `index.html`, `portfolio/portfolio.css`, and `blog/blog.css` each have the same `:root` token block. Change a colour in all three or they drift apart.
- **The CSP in `vercel.json` is strict.** `img-src` is `'self' data:`, so images hosted elsewhere will be blocked until you add their domain. Same for any third-party script or embed.
- **`.well-known/security.txt` expires 2027-09-30.** A GitHub Action opens a reminder issue each August. It currently lists only a LinkedIn contact — add an email when ready.
- **Google Analytics** is set up but inactive. Uncomment the GA4 block in the `<head>` of each page and add your measurement ID.

## To do

- [ ] Add the first portfolio project.
- [ ] Connect the `anabsilva.com` domain DNS to Vercel.
- [ ] Add an email to `.well-known/security.txt`.
- [ ] Set up Google Analytics measurement ID.
