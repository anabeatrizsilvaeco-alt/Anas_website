# anabsilva.com

Personal website of Ana Beatriz Silva, Data Analyst.

🌐 **[www.anabsilva.com](https://www.anabsilva.com/)**

## Tech stack

- **Stack**: plain HTML, CSS, and JavaScript. No build step, no dependencies.
- **Fonts**: Cormorant Garamond + DM Sans, loaded from Google Fonts.
- **Hosting**: Vercel (`vercel.json` holds the security headers), or GitHub Pages
  via `.github/workflows/static.yml`. Pick one and delete the other.

## Structure

```
index.html              Home — hero, about, expertise, certifications, connect
                        (all CSS is inline in the <style> block)
portfolio/
  index.html            Project list
  portfolio.css
  images/               Screenshots and GIFs for project cards
blog/
  index.html            Post list
  blog.css              Shared by the list and the posts
  post-template.html    Copy this per post, fill in the {{PLACEHOLDERS}}
  feed.xml              Atom feed, maintained by hand
assets/
  images/               profile.jpg, og-default.jpg (link preview card)
  img/favicons/         AB monogram, every size
```

## How to edit

### Add a project

Open `portfolio/index.html` and follow the `✏️` comment: uncomment the
`<section class="project-grid">` and copy one `.project-card` per project.
Newest goes on top. Drop the screenshot in `portfolio/images/`.

### Add a certification

Open `index.html`, find the Certifications section, delete the `.empty-state`
block and uncomment the `.cert-grid` beneath it.

### Publish a blog post

1. Copy `blog/post-template.html` to `blog/your-slug.html`.
2. Replace every `{{PLACEHOLDER}}` (the list is in a comment at the top of the file).
3. Add a `.blog-post-item` to `blog/index.html` and delete the `.blog-empty` block.
4. Add an `<entry>` to `blog/feed.xml` and bump its `<updated>` date.
5. Add the URL to `sitemap.xml`.

## Things to keep in mind

- **The colours live in one place per file.** Each of `index.html`,
  `portfolio/portfolio.css`, and `blog/blog.css` starts with the same `:root`
  token block. Change a colour in all three or they drift apart.
- **The CSP in `vercel.json` is strict.** `img-src` is `'self' data:`, so an
  image hosted somewhere else will be blocked until you add its domain. Same
  for any third-party script or embed.
- **`.well-known/security.txt` expires 2027-09-30.** A GitHub Action opens a
  reminder issue each August. It currently lists only a LinkedIn contact —
  add an email.
- **Set up Google Analytics** by uncommenting the GA4 block in the `<head>` of
  each page and dropping in the measurement ID.

## To do

- [ ] Rewrite the About and Expertise copy — the text in place is a draft
      written from the job title alone.
- [ ] Add an email to `.well-known/security.txt`.
- [ ] Add the first portfolio project.
- [ ] Point the `anabsilva.com` DNS at the host.
