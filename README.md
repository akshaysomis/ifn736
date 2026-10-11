# GEO Phase 2 Prototype

Static site for the GEO Phase 2 prototype (IFN736, Group 22). Deployed on GitHub Pages at
**https://elllllllle.github.io/ifn736-geo-project/**

- `/` — findings dashboard, grouped into three parts: **Part 1 — The Results** (headline mention
  rates, journey stage & competitors), **Part 2 — The Evidence** (pooled significance, run-by-run
  consistency across 4 team members, and a follow-up test on whether rewording the P2 FAQ-only
  page moves the needle further), **Part 3 — What It Means** (key takeaways, recommendations,
  limitations & caveats)
- `/chat/` — interactive chat demo — ask a travel question, compare Baseline vs Optimised
  (content-injected) responses from Gemini, with live Inclusion Rate / Ranking Position /
  rubric-score metrics per turn
- `/mockups/` — the 10 Flight Centre GEO mockup site variants used for V3 testing: an Incremental
  Comparison Ladder (Site A → V1 → V2 → Site B → V4) plus Isolated Technique Variants (P2, the
  restructured P2.1, P3, P4, P5), with a directory page linking to each
- `/queries/` — the 19 multi-turn test conversations run against every page variant, grounded in
  Flight Centre's Customer Persona Book and mapped to the Dream → Plan → Engage → Book (→ Pre-trip)
  journey

## Updating the live site

The repo is already set up and deployed — from this folder, committing and pushing to `main`
updates the live site within a minute or two:

```bash
git add -A
git commit -m "..."
git push origin main
```

GitHub Pages is configured under **Settings → Pages → Build and deployment → Source: Deploy from
a branch → Branch: main / (root)**.

<details>
<summary>First-time setup (already done for this repo — kept for reference)</summary>

```bash
git init
git add .
git commit -m "GEO Phase 2 prototype: dashboard, chat demo, mockup sites"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch →
Branch: main / (root)**. The site goes live at `https://<your-username>.github.io/<repo-name>/`
within a minute or two — dashboard at the root URL, chat demo at `/chat/`, mockup sites at
`/mockups/`, query set at `/queries/`.

</details>

## About the chat demo's API key

The chat page calls the Gemini API directly from browser JavaScript, so each visitor pastes in
their own Gemini API key rather than the site shipping a shared one. The key lives only in that
browser tab for the session (sent straight to Google with each request, never stored or sent
anywhere else) and has to be re-entered on reload. This keeps things simple for a static,
GitHub-Pages-hosted demo, but it does mean each visitor needs their own key and is on the free
tier's rate limits.

If this ever needs to run with one shared key instead (e.g. so visitors don't need their own),
the options are:

1. Keep the repo private (needs a paid GitHub plan for Pages on a private repo).
2. Use a separate, rate-limited key you're fine with someone eventually finding.
3. Put a small server-side proxy in front of it (e.g. a Cloudflare Worker) so the browser never sees the real key.
