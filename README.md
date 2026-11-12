# My Blog

A simple static blog built with plain HTML and CSS, deployed automatically with AWS Amplify every time code is pushed to GitHub.

## Project structure

```
my-blog/
├── index.html          # Home page with the list of posts
├── css/style.css       # Site styles (supports light and dark mode)
├── posts/
│   └── hello-world.html  # Sample post
├── amplify.yml         # AWS Amplify build settings
└── README.md
```

## Run locally

No build step is needed. Open `index.html` in a browser, or serve the folder so that root-relative links like `/css/style.css` work:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Add a new post

1. Copy `posts/hello-world.html` to a new file, e.g. `posts/my-second-post.html`.
2. Edit the title, date, and content.
3. Add a new `<li>` entry to the list in `index.html` linking to it.
4. Commit and push.

## Publish the code to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

## Deploy with AWS Amplify (auto-deploy)

1. Sign in to the [AWS Amplify console](https://console.aws.amazon.com/amplify/).
2. Choose **Create new app** → **GitHub** → **Next**, and authorize AWS Amplify to access your GitHub account.
3. Select this repository and the `main` branch.
4. Amplify detects `amplify.yml` automatically. Review the settings and choose **Save and deploy**.
5. When the build finishes, Amplify gives you a URL like `https://main.xxxxxx.amplifyapp.com`.

From now on, every `git push` to `main` rebuilds and redeploys the site automatically.

### Optional

- **Custom domain:** App settings → Domain management → Add domain.
- **Preview deployments:** App settings → Previews, to get a test URL for each pull request.
- **Friendly 404 page:** add a `404.html` and set a rewrite rule under App settings → Rewrites and redirects.

## Customize

- Replace "My Blog", "Your Name", and the GitHub link in each HTML file.
- Change colors and fonts at the top of `css/style.css` (the `:root` variables).

## License

MIT
