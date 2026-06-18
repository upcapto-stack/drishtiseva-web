# DrishtiSeva Web — Netlify deployment bundle

Pre-built static artifact of [`upcapto-stack/drishtiseva`'s `apps/web/`](https://github.com/upcapto-stack/drishtiseva) — the source is in the monorepo, this repo holds only what Netlify needs to serve.

## Deploying on Netlify

1. New site → Import from GitHub → select `drishtiseva-web`
2. **No build command** (already built)
3. **Publish directory:** `.` (repo root)
4. **Deploy**

## Before the first deploy

`_redirects` proxies API calls to Railway. The Railway URL is a placeholder — find your real one in the Railway dashboard (service → Settings → Networking → Public Domain) and replace `REPLACE-WITH-RAILWAY-URL` in `_redirects`. The build itself doesn't need to change.

## Re-building

Anything that changes in the source repo requires re-running:

```sh
cd ~/Desktop/drishtiseva/apps/web && npm run build
cp -r dist/* ../../../drishtiseva-web/
cd ~/Desktop/drishtiseva-web && git add -A && git commit -m "rebuild" && git push
```

Netlify auto-deploys on push.
