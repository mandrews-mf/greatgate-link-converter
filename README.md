# Great Gate → Public Link Converter

A tiny, dependency-free static tool that turns gated **Great Gate** lesson links into their public asset URLs.

## What it does

A gated link wraps the public asset URL inside a `url=` query parameter:

```
https://greatgate.greatfirsteight.org/s/lesson?url=%2F%2Fpub.marq.com%2F1efa1727-...%2FembedControls.html&lessonName=...
```

The tool:
1. Reads and URL-decodes the `url` parameter
2. Strips the trailing `/embedControls.html`
3. Returns the public base URL — e.g. `https://pub.marq.com/1efa1727-...`

Supports **Marq** (`pub.marq.com`) and **CloudFront** (`*.cloudfront.net`) assets, single or batch (one link per line), with per-link and copy-all buttons.

> Note: the public link's `#fragment` (e.g. `#RMnsejvHBH1y`) lives only client-side and is **not present** in the gated link, so it cannot be recovered. The base URL works on its own.

## Running

It's a single `index.html` — open it in a browser, or serve the folder. Everything runs client-side; nothing is sent anywhere.

## Deploy

Live at **https://greatgate-link-converter.netlify.app** (Netlify, Marketing team).

Deployed via the Netlify CLI:

```
netlify deploy --prod --dir=.
```

`netlify.toml` sets the publish directory to the repo root with no build step. To switch to push-to-deploy, connect the repo under the Netlify site's **Build & deploy → Continuous deployment** settings.
