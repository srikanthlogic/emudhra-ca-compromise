# emudhra-ca-compromise

CashlessConsumer consumer guide and public record for the October 2026 eMudhra CA key compromise: eight intermediate certificates whose private keys carried 3–8 bits of randomness (one was literally `4`), reported 17 Oct 2026, distrusted by Firefox/Chrome within hours and Apple on 19 Oct — with no public word from any Indian authority.

**Live site:** https://srikanthlogic.github.io/emudhra-ca-compromise/

## Pages

| File | What it is |
| --- | --- |
| `index.html` | Consumer guide: what happened, timeline, who is protected/exposed, do-this-today checklist, verified India exposure, curated video explainers, sources |
| `statement.html` | CashlessConsumer public statement (v3) |
| `letter.html` | Open letter to RBI and MeitY (CC CCA, CERT-In, IDRBT, UIDAI, GeM, NPCI, browser root programs, eMudhra) |

## Sources of truth

- Statement + letter text: `statement-src.md` / `letter-src.md` (canonical master: `Kaarana/notes/2026-10-21-emudhra-statement-open-letter-rbi-meity.md` in the Zo workspace, which must pass `Skills/cc-comms-voice/scripts/tells.py`)
- Rebuild the HTML doc pages: `pandoc statement-src.md -f markdown -t html` → body → `python3 build_pages.py` (assembles around the site template)
- Research basis: Kaarana explainer https://cashlessconsumer.zo.space/kaarana/2026-10-21-emudhra-ca-compromise and desk verification (live TLS handshakes, 20–21 Oct 2026)

## Deploy

Plain static HTML/CSS, no build step. Two paths:

1. **Deploy from branch (current):** enable once in repo Settings → Pages → Source: *Deploy from a branch* → `main` / `(root)`. Site: https://srikanthlogic.github.io/emudhra-ca-compromise/
2. **Actions deploy (needs workflow scope):** `.github/workflows/pages.yml` is prepared locally (not pushable via the Pipedream OAuth token, which lacks the `workflow` scope). Once Pages is enabled or a workflow-scoped token is connected, push it and every push to `main` redeploys (configure-pages `enablement: true`).

Voice rule: all public copy on this site must pass the CashlessConsumer comms-voice gate — no agentic tells (run `tells.py` on extracted text before publishing changes).
