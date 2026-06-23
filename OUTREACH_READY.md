# Outreach gate — GOTOWE DM-y do wysłania (2026-06-23)

> Cel: pierwsze rozmowy z ludźmi krwawiącymi z runaway-cost agentów (ICP z council).
> Każdy DM = spersonalizowany pod konkretne ich issue. Ty robisz JEDEN ruch: wklej + wyślij.
> Landing w linku: https://mesh.bgml.ai/gate/
> ⚠️ Wysyłka pod Twoją tożsamością = Twoja decyzja per wiadomość. Treść gotowa, nie spamuj — wyślij do tych, gdzie ból realny.

## ZASADA (council): NIE "router/uncertainty gate". Mów o ICH bólu + liczbie z trialu.
Pierwsza wiadomość = pytanie, nie pitch. Słuchasz czy "cap wystarcza" (vitamin) czy "cap tnie dobre taski / przepalamy" (painkiller).

---

## LEAD 1 — redasadki (openclaw/openclaw #95985)
**Ból:** cacheWrite spiral, $305.49 w 24h, 14.8M cache writes. Najostrzejszy z całej listy.
**Gdzie:** komentarz pod issue #95985 LUB GitHub profile → email/social.
**DM (EN, komentarz pod issue):**
> $305 in 24h from a cache-write spiral is exactly the failure mode I'm working on — the agent doesn't know it's stuck, so it keeps writing. A `max_steps` cap won't catch it because the model is confident, not verbose.
>
> I built a proxy layer that measures when the model is actually uncertain (sample disagreement, not output length) and pauses/escalates before the spend. Curious: how are you catching these spirals today — hard caps, or something smarter? And roughly what's the monthly bleed even with caps on?
>
> (If useful: https://mesh.bgml.ai/gate/ — but mostly I want to know if a hard cap is "good enough" for you or not.)

---

## LEAD 2 — tonytan4ever (flowforge-lab/FlowForge #394)
**Ból:** prosi o thinking_budget żeby cap-nąć runaway reasoning cost. Sam szuka rozwiązania = ciepły lead.
**DM:**
> Saw your thinking_budget request — capping runaway reasoning by a fixed budget works, but it also cuts off good long reasoning at the wrong moment. I'm testing a different angle: gate on *measured uncertainty* (does the model agree with itself across samples) instead of a fixed token ceiling — so it only stops the runs that are actually guessing.
>
> Does a flat thinking_budget solve it for you, or does it kill tasks that legitimately need the tokens? Genuinely asking — trying to learn if the smarter gate is worth building for teams like yours.

---

## LEAD 3 — tonitienda (tonitienda/agent-smith #385)
**Ból:** chce per-child cost itemization + budget ceiling dla subagentów.
**DM:**
> Your per-child budget ceiling issue is the right instinct — but a ceiling is blunt: it caps the subagent that's working fine alongside the one that's looping. I'm building a layer that flags *which* subagent is actually uncertain (not just which one spent most) so you escalate the guessing one, not the busy one.
>
> How much of your subagent spend is genuinely runaway vs just expensive-but-correct? That ratio decides whether a smart gate beats a flat ceiling.

---

## LEAD 4 — sethdford (sethdford/shipwright #681)
**Ból:** proponuje live budget alerts + auto-downshift.
**DM:**
> Your auto-downshift idea is close to what I'm building — but the trigger matters. Downshifting on $ spent reacts after the burn; downshifting on *measured uncertainty* reacts before it. I gate on sample disagreement (model disagreeing with itself = guessing) and escalate/pause then.
>
> Is your downshift trigger cost-based or quality-based right now? And does it ever downshift a task that was actually fine?

---

## KANAŁY (szersze, gdy 4 powyżej odpiszą lub nie)
- r/LLMDevs — wątek "how do you cap runaway agent spend?" (pytanie, nie reklama; link w komentarzu gdy ktoś pyta)
- Discord: Aider #general, OpenHands #help, LangChain #agents — szukaj "$" / "cost" / "loop" w ostatnich wiadomościach, odpowiadaj konkretem
- GitHub: szukaj `runaway cost agent` sortuj updated → nowe issue co tydzień = świeże leady

## PRÓG DECYZYJNY (council)
≥3 z odpowiedzi mówi "cap wystarcza" → vitamin, pivot (FinOps/EU-regulated).
≥3 mówi "cap tnie dobre taski / wciąż przepalamy" → PAINKILLER, buduj proxy-trial dla tych 3.
