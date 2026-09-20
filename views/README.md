# Views

Static HTML mockups for exploring the sample data in [`data/`](../data/).

- `certifications_mockup.html` — certifications grouped by `cert_type`, joined with crew info, with search/status/crew filters.
- `crew_mockup.html` — crew roster grouped by `rank`, with search/status/base/crew filters.

The two pages cross-link by `crew_id` (e.g. clicking a crew name on the certifications page filters the crew page to that person, and vice versa).

## Startup

These pages use `fetch()` to load `../data/*.json`, so they must be served over HTTP — opening them directly via `file://` will fail due to CORS.

From the project root, run a static server:

```powershell
npx --yes serve -l 8080
```

Then open:

- http://localhost:8080/views/certifications_mockup.html
- http://localhost:8080/views/crew_mockup.html

Any other static server (e.g. `python -m http.server 8080`, VS Code's "Live Server" extension) works too, as long as it's started from the project root so `../data/*.json` resolves correctly.

> Note: `serve`'s "clean URLs" redirect can strip query strings from `.html` links. Both pages already fall back to parsing the crew id from the URL hash (`#crew-<id>`) if the query string is missing.
