# Portfolio site (GitHub Pages)

A plain HTML/CSS site: no build step, no paid services. Open `index.html` in a browser to preview it.

```
portfolio/
  index.html              home page: intro, project cards, experience, skills
  projects/*.html         one page per project
  assets/style.css        all styling (light + dark)
  assets/theme.js         light/dark toggle
  images/<project>/       put each project's images here
  .nojekyll               tells GitHub Pages to serve the files as-is
```

## Before you publish: check these

1. **Employment or personal?** Each project page has a "My role" badge that says *To be confirmed*. Replace it with
   `Employment project · SIMUT` or `Personal project` (the exact HTML is in a comment next to the badge).
2. **Confidentiality.** If a project was SIMUT (or any employer's) work, check that your employer and any NDA
   allow you to publish its images, schematics and specs. When in doubt, show less: a blurred or partial
   layout, a stack-up diagram without part numbers, or just a text description.
3. **Fill in the "to be added" items** only with facts you can back up. Then delete the yellow *Draft* note
   at the top of each project page.
4. **Job titles.** The experience list uses the titles from your newest CV. Some differ between CV versions
   (see the `UNCONFIRMED` notes in `config/profile.yaml`); fix them here if needed.
5. Your phone number is deliberately left off the public site.

## Publish on GitHub Pages (free)

1. Create a GitHub account if you don't have one: <https://github.com/signup>.
2. Create a new **public** repository named exactly `<your-username>.github.io`
   (e.g. `mazizi.github.io`). Don't add a README; this folder already has one.
3. Push this folder's contents to it. From inside `portfolio/`:

   ```bash
   git init
   git add .
   git commit -m "First version of portfolio site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
   git push -u origin main
   ```

   (No command line? On the new repo page click **uploading an existing file** and drag in the contents of
   `portfolio/`, keeping the folders.)
4. In the repo go to **Settings → Pages**. Under **Build and deployment**, set **Source** to
   *Deploy from a branch*, branch **main**, folder **/ (root)**, then **Save**.
5. After a minute or two the site is live at `https://<your-username>.github.io/`.
   The Pages settings screen shows the link once it's ready.

To update the site later: edit the files, then `git add . && git commit -m "..." && git push`.

## Add images

1. Export from your EDA tool (e.g. Altium: 3D view screenshot, or *File → Export* / *Smart PDF* for layers).
2. **Keep files small** so the site stays fast:
   - About **1600 px wide** is plenty for a full-width image; ~800 px for card thumbnails.
   - Save as **WebP** (or JPG for photos, PNG only for sharp line art). Aim for **under 300 KB** per image.
   - Free tools: <https://squoosh.app> (in the browser) or GIMP.
   - Crop to the board; dark-background layout views read well in both themes.
3. Put the files in the project's folder, e.g. `images/hvsb/layout-top.webp`.
4. In the project page, replace a grey placeholder `<div class="ph">…</div>` with the `<img>` line shown
   in the comment above the gallery. Set `width` / `height` to the image's real pixel size and write a
   short `alt` text describing it.
5. For the home page card, replace `<div class="thumb">Image coming soon</div>` in `index.html` with the
   commented example under the first card.
6. Remove any metadata or internal part/project numbers you're not allowed to share before uploading.

## Add another project

Copy one of the files in `projects/`, rename it (lowercase, hyphens), edit it, and add a matching
`<a class="card">…</a>` block to the **Selected PCB projects** section of `index.html`.

## Connect it to the job bot

Once the site is live, set the URL in `config/profile.yaml` (one folder up):

```yaml
contact:
  website: https://<your-username>.github.io/
  github: https://github.com/<your-username>
```

The bot's cover letters will then include the portfolio link, and application forms that ask for a
website or GitHub profile get these answers.
