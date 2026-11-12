# Project websites

Primary URL: https://project.juyujing.com/

GitHub repository: https://github.com/juyujing/project

GitHub Pages default URL: https://juyujing.github.io/project/ (redirects to the primary domain).

GitHub Pages does not provide nested hostnames such as `project.juyujing.github.io`.

## Where to put website content

- Replace `index.html` for the project portal homepage.
- Put each standalone website in a separate folder, for example `demo/index.html` and `demo/assets/`.
- That website will be available at `https://project.juyujing.com/demo/`.
- Use relative asset URLs (`./assets/image.jpg`) so each website works in its folder.
- Never commit passwords, tokens, private datasets, or local environment files to this public repository.

## Preview locally

Run from this directory:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open http://127.0.0.1:8000/ or http://127.0.0.1:8000/demo/.

## Publish

```sh
gh auth switch --user juyujing
git add .
git commit -m "Publish project content"
git push origin main
```

GitHub Pages publishes `main` from `/ (root)` automatically. Keep the `CNAME` and `.nojekyll` files.

## Domain

Cloudflare CNAME: `project` → `juyujing.github.io`. GitHub routes requests for `project.juyujing.com` to this repository via the tracked CNAME file. Cloudflare proxying should only be enabled after GitHub's domain certificate has been issued; use Full (Strict).
