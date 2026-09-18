# Fortuna People Solutions — Quarterly Newsletter

Source files for "The Fortuna Update", the quarterly HR / IR & ER / WHS client newsletter.

## Structure

Each issue lives in its own dated folder, e.g. `2026-09-issue-01/`:

- `newsletter.html` — the editable source (content + styling). Update the text here each quarter.
- `assets/` — logo and any other images used by the newsletter.
- `Fortuna-People-Solutions-Newsletter-Issue0X-<Month><Year>.pdf` — the rendered, client-ready PDF.

## Producing a new issue

1. Copy the most recent issue folder to a new dated folder (e.g. `2026-12-issue-02/`).
2. Update the content in `newsletter.html`:
   - IR & ER Update — latest Fair Work / industrial relations developments
   - Award Compliance Corner — current quarter's award/pay rate checks + a client case study
   - WHS & Safety Focus — current WHS/safety developments (national + WA-specific)
   - Respect@Work / other legislative spotlight
   - How Fortuna Can Help — keep in sync with the current Capability Statement
   - Update the issue number, month/year, and "looking ahead" teaser
3. Render to PDF with headless Chromium (no other dependencies required):

   ```bash
   cd newsletters/<issue-folder>
   /opt/pw-browsers/chromium-1194/chrome-linux/chrome \
     --headless --disable-gpu --no-sandbox --disable-dev-shm-usage \
     --print-to-pdf="Fortuna-People-Solutions-Newsletter-IssueXX-<Month><Year>.pdf" \
     --print-to-pdf-no-header \
     "file://$(pwd)/newsletter.html"
   ```

   (If Chromium isn't at that path in a future environment, any Chrome/Chromium binary with
   `--headless --print-to-pdf` works the same way.)

4. Spot-check the PDF (page count, no overflow/blank spillover pages) before sending to clients.

## Notes

- Page size is A4, designed to print cleanly as a ~6-page PDF.
- Brand colours (blue/teal/green) are pulled from the Fortuna diamond logo and defined as CSS
  variables at the top of `newsletter.html` — keep these in sync with the brand.
- All legislative/regulatory content should be sourced from primary sources (Fair Work Commission,
  Fair Work Ombudsman, Safe Work Australia, WorkSafe WA, ATO, AHRC) and re-verified each quarter —
  don't just re-date the previous issue's content.
