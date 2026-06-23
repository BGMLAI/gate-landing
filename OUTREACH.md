# Gate — aparat outreach (pierwszy ruch, walidacja painkiller)

> Cel: 5 rozmów + sygnał z fake-door, ZANIM napiszesz linijkę kodu produktowego.
> Próg decyzyjny: ≥3/5 "cap tnie nam dobre taski / wciąż przepalamy" → painkiller, budujesz proxy-trial dla tych 3.
> ≥3/5 "cap wystarcza" → vitamin, pivot (EU-regulated/FinOps).

## GDZIE szukać leadów (pre-kwalifikowani — już publicznie płaczą o rachunki)

1. **GitHub issues** — szukaj w repo agentów po słowach: `runaway`, `infinite loop`, `token cost`, `cost explosion`, `burned $`, `budget`
   - github.com/All-Hands-AI/OpenHands/issues
   - github.com/Aider-AI/aider/issues
   - github.com/princeton-nlp/SWE-agent/issues
   - github.com/cline/cline/issues
   - Autor issue z firmowym profilem / agency w bio = lead.
2. **r/LLMDevs, r/LocalLLaMA** — wątki "my agent burned $X", "how to cap agent cost"
3. **Discord** — kanały #cost / #help na serwerach Aider, LangChain, OpenHands, CrewAI
4. **X/Twitter** — indie buildujący "Devin alternative" / "autonomous coding agent" chwalący się projektami klienckimi

## PYTANIE WALIDACYJNE (jedno, w rozmowie — NIE ankieta)

> "Jak teraz łapiecie runaway agenta — twardy max_steps, czy coś mądrzejszego? I ile $/mc to realnie kosztuje MIMO capa?"

Słuchasz JEDNEJ rzeczy:
- "mamy cap i wystarcza" → gate martwy (vitamin)
- "cap tnie nam dobre taski / wciąż przepalamy" → jest ból którego cap nie rozwiązuje (painkiller)

## 5 DM — szablony (dopasuj do konkretnego issue/postu)

### DM-1 — odpowiedź pod GitHub issue o runaway-cost (publiczna, wartość najpierw)
> Widziałem twój issue o [runaway/token cost]. Szybkie pytanie z ciekawości — łapiecie to twardym max_steps, czy
> macie coś co wykrywa KIEDY agent brnie w złą ścieżkę zanim utnie? Bo cap zwykle albo tnie za wcześnie, albo za późno.
> Buduję warstwę która mierzy niepewność modelu (nie długość outputu) i zatrzymuje zanim spali budżet — ciekaw jak
> wy to rozwiązujecie. (zero sprzedaży, realnie pytam)

### DM-2 — DM do autora po jego odpowiedzi (jeśli ból potwierdzony)
> Dzięki. Brzmi jak dokładnie ten problem. Mam proxy OpenAI-compatible które wpinasz jedną linijką (base_url) i puszczasz
> na swoich logach 2 tygodnie za darmo — pokazuje ile $ runaway by uciął, na TWOICH danych. Bez karty, bez zobowiązań.
> Chcesz wcześniejszy dostęp? Interesuje mnie głównie czy liczba w dashboardzie cię przekona.

### DM-3 — zimny, do agency z bio "autonomous coding agents"
> Hej [imię] — robicie [autonomous coding / Devin-alt] na repo klientów. Pytanie: ile miesięcznie zżerają runaway-loopy
> (agent brnie w złą ścieżkę, pali tokeny, ktoś musi zauważyć)? Buduję warstwę która to wykrywa po niepewności modelu,
> nie po długości outputu — retry-if-short tego nie łapie. Trial na waszych logach, darmowy. Wart 10 min rozmowy?

### DM-4 — Reddit/Discord, pod wątkiem "my agent burned $X"
> Ten ból jest realny i cap go nie rozwiązuje (tnie dobre taski / puszcza confident-but-wrong loopy). Pracuję nad proxy
> które eskaluje TYLKO gdy model faktycznie niepewny. Jak chcesz przetestować na swoich logach — DM, dam early access.
> Ciekaw głównie ile $ by ci uciął.

### DM-5 — follow-up po trialu (gdy ktoś już puścił na logach)
> Jak wygląda liczba w dashboardzie po 2 tyg? Ile $ runaway by uciął? Jeśli wyszło sensownie — $299/mc flat za hosting
> progów + dashboard. Jeśli nie — powiedz wprost, to dla mnie sygnał że jeszcze nie tam.

## TON (z badań usera — anti-overclaim)
- NIE "router LLM", NIE "uncertainty gate" — mów REZULTATEM: "przestaje palić budżet na pętlach".
- NIE obiecuj "rozwiązuje halucynacje" — to malpractice (gate ≠ 1.0). Mów "redukuje runaway-spend, mierzone na twoich logach".
- Wartość PRZED prośbą: najpierw pytanie/pomoc, potem trial, dopiero potem cena.

## METRYKA (fake-door + rozmowy)
- Landing: emaile w localStorage/`/api/lead` = sygnał kupna (NIE lajki).
- 5 rozmów: zapisz odpowiedzi tu (cap-wystarcza vs cap-tnie-dobre). Próg ≥3/5.
- Po walidacji: jeśli painkiller → Faza 0 (ożyw gate w aggregator.py) dla tych 3 konkretnych.
