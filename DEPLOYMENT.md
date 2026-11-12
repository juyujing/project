# Deployment configuration

- Repository: `juyujing/project` (public).
- Local checkout: `/Users/yuzuki/Documents/ChatGPT/profile/juyujing-project`.
- Source: GitHub Pages, `main`, repository root.
- Primary domain: `project.juyujing.com`.
- Default Pages entry: `https://juyujing.github.io/project/`, redirected to the custom domain.
- Cloudflare DNS: CNAME `project` to `juyujing.github.io`.
- Cloudflare configuration rule: `Project HTTPS - Full Strict`, matching only `http.host eq "project.juyujing.com"`, with SSL Strict. The parent domain's existing encryption mode is preserved.

## Setup status — 2026-11-12

The portal source is committed and deployed. Public DNS returns the new CNAME, and GitHub's DNS check has passed. A subsequent Pages build was requested after an earlier generic build error and completed successfully.

GitHub's domain certificate is still pending in state `new`. The project DNS record remains DNS-only while the origin certificate is being issued. Do not claim HTTPS is live or enable proxying with an invalid origin certificate.

Once the certificate is approved:

1. Enable Enforce HTTPS for `juyujing/project`.
2. Check HTTPS certificate validation for `project.juyujing.com`.
3. Enable Cloudflare proxying for the `project` CNAME only.
4. Verify the project portal, its assets, HTTP-to-HTTPS redirection, and the default GitHub Pages URL.
5. Update this status after verification.

## Content layout

```text
juyujing-project/
  index.html          # Project portal homepage
  CNAME               # Keep this custom-domain binding
  .nojekyll           # Keep this for static files
  demo/
    index.html        # https://project.juyujing.com/demo/
    assets/
```

The `demo` directory is an example layout, not a pre-created published project. Copy each website's built static files into its own folder. Commit and push to `main` to publish; no further DNS changes are needed for folders.
