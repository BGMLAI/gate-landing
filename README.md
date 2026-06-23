# gate-landing — fake-door + lead capture

Pierwszy ruch firmy gate: waliduj painkiller ZANIM piszesz kod produktowy.

## Co to jest
- `index.html` — fake-door landing (pitch dla coding-agent agencji, email capture). Działa standalone.
- `functions/api/lead.js` — Cloudflare Pages Function odbierająca leady (webhook + KV).
- `OUTREACH.md` — 5 DM-ów + kanały + pytanie walidacyjne + próg ≥3/5.
- `wrangler.toml` — config deployu.

## URUCHOMIENIE (3 polecenia, ~5 min) — wymaga konta Cloudflare usera

```bash
cd gate-landing
npx wrangler login                    # jednorazowo, otwiera przeglądarkę
npx wrangler pages deploy .           # publikuje → dostajesz URL *.pages.dev
```

Po deployu: ustaw notyfikację leadów (opcjonalnie, ale zalecane):
- Cloudflare dashboard → Pages → gate-landing → Settings → Environment variables
- dodaj `LEAD_WEBHOOK` = URL incoming-webhook Slack lub Discord
- leady będą wpadać na czacie w czasie rzeczywistym

Health check po deployu: `curl https://<twoj-url>.pages.dev/api/lead` → `{"ok":true}`.

## PO DEPLOYU — ruch usera (AI tego nie zrobi)
1. Skopiuj URL landingu.
2. Wyślij 5 DM-ów (OUTREACH.md) ze swojego GitHub/Discord — wklej link do landingu.
3. Przeprowadź 5 rozmów. Zapisz: "cap wystarcza" vs "cap tnie dobre taski / przepalamy".
4. Próg: ≥3/5 painkiller → wracasz do kodu (Faza 0: ożyw gate w aggregator.py).
       ≥3/5 vitamin → pivot (EU-regulated/FinOps, patrz GATE_VENTURE_COUNCIL).

## Dlaczego fake-door przed kodem
Council 5-modeli (docs/GATE_VENTURE_COUNCIL_2026-06-23.md): bottleneck NIE jest wykonanie
(AI je rozwiązuje), tylko czy ktoś ZAPŁACI. Fake-door + 5 rozmów = $0 test czy to painkiller,
zanim wydasz dzień na proxy. Sygnał kupna = emaile/odpowiedzi, NIE lajki.
