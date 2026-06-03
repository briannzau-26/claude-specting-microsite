# Claude-specting Microsite

A single-file enablement microsite for **Claude-specting**, Envoy's prospecting copilot. It is a self-contained `index.html` (vanilla HTML, CSS, and JS, no build step, no backend) covering what the assistant does, quick-start paths, use cases, org-chart guidance, Fast Track vs Value Track, a scavenger hunt, a prompt library, and an FAQ.

## What's here

- `index.html` — the entire site. Inline `<style>` and `<script>`, with one external dependency: the Google Fonts stylesheet. No frameworks, no API calls, no analytics.
- `amplify.yml` — pre-staged build spec for an eventual AWS Amplify migration (see below).
- `README.md` — this file.

## Hosting

Hosting currently runs on **GitHub Pages**, served from the repo root on `main`. `index.html` at the root is the Pages entry point. Any push to `main` redeploys automatically.

To run locally, open `index.html` in a browser, or serve the directory:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Editing the prompts

Every copyable prompt appears **twice**: once as visible card text and once in a `data-copy` attribute on its copy button. The two must stay identical. After editing any prompt, confirm the visible text and its `data-copy` value still match before committing.

## Migrating to AWS Amplify

This is a static single-file site, so migration is low effort: point an **AWS Amplify Gen 2** app at this repo and let it use the included `amplify.yml`. There is no build step and no code changes are required. The spec declares no build commands and publishes the repo root (where `index.html` lives) as the artifact directory.

Hosting currently runs on GitHub Pages and can cut over to Amplify under the Envoy org whenever infra (Tanya / Ani) is ready. Nothing in the site depends on the host, so the cutover is purely a DNS / hosting change.

Link - https://briannzau-26.github.io/claude-specting-microsite/
