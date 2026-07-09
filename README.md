# GEO Opportunity Rating (blind)

Shareable blind-rating app for GEO opportunities across two accounts (Twix,
syncplacement). Each account shows 21 opportunities drawn from 3 prompt versions
(v1/v2/v3, 7 each), shuffled with blind ids. Raters never see the prompt version.

- **Public app:** served by GitHub Pages from this repo's root (`index.html`).
- **Shared datastore:** ratings are POSTed by the browser to an ntfy.sh topic
  (see `config.json`). BLIND only — no prompt_version leaves the browser.
- **Durable archive:** `.github/workflows/archive-ratings.yml` polls the topic every
  30 min and appends new messages to `ratings-raw.jsonl` (blind).
- **Reading results + prompt_version:** done off-repo with the private key file and
  `apps/opp-rating-web/read-ratings.ts` in the gist-geo repo. prompt_version is
  re-attached only there, never here.

Do NOT commit any `opps-key.json` to this repo — it would break the blind.
