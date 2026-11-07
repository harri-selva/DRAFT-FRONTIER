# FRONTIER interactive prototype

Open `dist/index.html`  for the visual prototype and offline abstract composition.

The journey is galaxy → field surface → research-area islands → 3D paper-cluster network. Drag to orbit, Shift-drag to pan, scroll to zoom. The 2D directory and graph remain available.

## Run the local server

Requires Node.js 22 or newer. From this directory:

```sh
node server.mjs
```

Open http://127.0.0.1:4173 in a browser. Without model configuration, offline draft generation works and Live AI reports that setup is required.

## Enable live AI

Configure `OPENAI_API_KEY` and `OPENAI_MODEL` in the server environment using the approved OpenAI Developers setup. Do not put keys in the HTML, client-side settings, or this README. Restart the server after configuring access.

If you choose to use a local `.env` file, copy `.env.example`, fill it securely, keep it untracked, and start with:

```sh
node --env-file=.env server.mjs
```

Live AI uses OpenAI's Responses API. It sends the selected sample gap, the optional research aim, chosen format/length, and literature text explicitly provided in the abstract workspace. It does not send API keys to the browser. Requests use `store: false`; this does not override provider retention policies. The loopback server validates request origins and limits request size/concurrency.

No live model call has been verified until model access is connected. Live generation is never silently replaced with an offline draft.

## Prototype limitations

Papers, counts, suitability scores, and relationships are illustrative. The 3D network represents paper communities, not the prediction model's internal neural-network architecture. Offline drafts are deterministic compositions of the selected gap and study plan. Both offline and AI drafts describe proposed studies, not completed results.

## Edit and rebuild

Editable interface sources live in `src/`. Run `npm run build` to regenerate the standalone `dist/index.html` and sample `data.json`; then run `npm start` for the local server. No dependency installation is required.

Model access is not yet configured. All scientific data are illustrative.

## Public demo deployment

GitHub Pages serves the standalone `index.html` from the root of `main`. The static demo includes offline abstract drafting. GitHub Pages does not run `server.mjs`, so live AI requires deploying the backend separately with server-side model access.

`npm run build` regenerates both `dist/index.html` and the root `index.html`.
