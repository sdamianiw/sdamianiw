Chemical engineer turned applied-AI engineer: I build agentic systems, RAG pipelines and LLM automation for industry and energy, and I ship them end to end: parsers, evals, Docker, the boring parts. Currently AI Catalyst at DGD (Dominion) in Essen, Germany, a Chilean working in German industrial contexts.

Open to AI engineering / forward-deployed roles, EU/remote.

## Selected work

**[chemtrace](https://github.com/sdamianiw/chemtrace)**: Local-first Scope 1-2 carbon accounting for German industrial SMEs facing CSRD reporting: parses energy invoices and SAP CSV exports, computes CO2e, answers questions over the data.  
Receipt: runs with zero cloud dependencies and zero API keys; exports to the EFRAG VSME Digital Template v1.2.0; 73 unit + 2 integration tests gate every PR.  
Stack: Python 3.11, Ollama (`llama3.2:3b`), ChromaDB, `all-MiniLM-L6-v2` embeddings, Docker Compose. MIT.

**[pollagol-sim](https://github.com/sdamianiw/pollagol-sim)**: Dixon-Coles bivariate Poisson forecaster for the 2026 World Cup, with an optimizer that maximizes expected points under the pool's scoring rubric rather than picking the modal scoreline.  
Receipt: finished 1st of 27 in the pool, 410 points vs 386 for second, over 104 predicted matches; backtest verdict PASS (delta +0.044, n=5402) and the ledger records that the frozen model alone would have placed 2nd: the human-gated overrides made the difference.  
Stack: Python, common-random-numbers Monte Carlo on a fixed seed, The Odds API ingest, 269 tests.

**[chilecompara](https://github.com/sdamianiw/chilecompara)**: Cross-retailer smartphone price comparison for Chile. The scraping is the easy half; the real problem is deciding that two differently worded listings are the same phone, with rules general enough to match a model that does not exist yet.  
Receipt: 3 retailers (Falabella, Paris, Ripley) unified into one catalog by 7 containers, rebuilt from raw offers on every event so partial-state bugs cannot exist; 978 Go LOC, 685 TypeScript LOC.  
Stack: Go unifier and API, TypeScript + Playwright scrapers, Redis as the only datastore, nginx portal, Docker Compose.

**[greenreceipt](https://github.com/sdamianiw/greenreceipt)**: React Native app for the German market: photograph product packaging, OCR it on-device, classify the environmental claims into Vague / Verifiable / Unsupported / Substantiated.  
Receipt: OCR runs on-device via ML Kit so no images leave the phone; the OpenAI key lives only in the Edge Function; `scans` table is RLS deny-all for anon; 20 scans/device/24h enforced server-side.  
Stack: Expo SDK 54, React Native 0.81.5, TypeScript, Supabase Edge Function calling `gpt-5-nano` through the Responses API with a strict JSON schema.

## How I work

- Every number in my repos has a command next to it that reproduces it, and if I cannot run the command I delete the number: chilecompara's README lost its live catalog counts for exactly that reason.
- I write the limitations section before the features section: chilecompara documents that Ripley needs a manual cookie that expires in ~30 minutes and that only a few listing pages per retailer are read.
- Evals before prompts. pollagol-sim's backtest (n=5402) and calibration numbers (Brier 0.579, 11.6% exact-hit rate) were run before I trusted the optimizer with a live season.
- I write the one-way data flow into the repo contract as a named invariant: no code path in pollagol-sim may read a match result and write back a model parameter.
- I put safety rules in the prompt contract, not in a postscript: greenreceipt's classifier is forbidden from words like "greenwashing" or "Betrug" and is instructed to downgrade its verdict when uncertain.
- I default to local and reproducible where the domain allows it: chemtrace runs entirely on the user's machine, with emission factors in a JSON file that cites its source, so a new energy type needs no code change.

## Elsewhere

LinkedIn: [linkedin.com/in/sebastián-damiani-wolf](https://www.linkedin.com/in/sebasti%C3%A1n-damiani-wolf-753b95251)  
Essen, Germany. Open to EU/remote.
