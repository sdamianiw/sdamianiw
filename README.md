# Sebastián Damiani Wolf

Chemical engineer turned applied-AI engineer. I build agentic systems, RAG pipelines and LLM automation for industry and energy, and I ship them myself, down to the parsers and the Docker files. I work as AI Catalyst at DGD (Dominion) in Essen, Germany, a Chilean in German industrial contexts.

## Selected work

**[chemtrace](https://github.com/sdamianiw/chemtrace)**: Local-first Scope 1-2 carbon accounting for German industrial SMEs facing CSRD reporting. It parses energy invoices and SAP CSV exports, computes CO2e, and answers questions over the data.  
Receipt: runs with zero cloud dependencies and zero API keys; exports to the EFRAG VSME Digital Template v1.2.0; 155 tests gate every PR.  
Stack: Python 3.11, Ollama (`llama3.2:3b`), ChromaDB, `all-MiniLM-L6-v2` embeddings, Docker Compose. MIT.

**[pollagol-sim](https://github.com/sdamianiw/pollagol-sim)**: Dixon-Coles bivariate Poisson forecaster for the 2026 World Cup. The optimizer maximizes expected points under the pool's scoring rubric instead of picking the modal scoreline.  
Receipt: finished 1st of 27 in the pool, 410 points against 386 for second, over 104 predicted matches; backtest verdict PASS (delta +0.044, n=5402), and the ledger records that the frozen model alone would have placed 2nd, so the human-gated overrides made the difference.  
Stack: Python, common-random-numbers Monte Carlo on a fixed seed, The Odds API ingest, 269 tests.

**[chilecompara](https://github.com/sdamianiw/chilecompara)**: Cross-retailer smartphone price comparison for Chile. The scraping is the easy half. The real problem is deciding that two differently worded listings are the same phone, with rules general enough to match a model that does not exist yet.  
Receipt: 3 retailers (Falabella, Paris, Ripley) unified into one catalog by 7 containers, rebuilt from raw offers on every event so partial-state bugs cannot exist; 978 Go LOC, 685 TypeScript LOC.  
Stack: Go unifier and API, TypeScript + Playwright scrapers, Redis as the only datastore, nginx portal, Docker Compose.

**[greenreceipt](https://github.com/sdamianiw/greenreceipt)**: React Native app for the German market. Photograph product packaging, OCR it on-device, classify the environmental claims into Vague / Verifiable / Unsupported / Substantiated.  
Receipt: OCR runs on-device via ML Kit, so no images leave the phone; the OpenAI key lives only in the Edge Function; the `scans` table is RLS deny-all for anon; 20 scans/device/24h enforced server-side.  
Stack: Expo SDK 54, React Native 0.81.5, TypeScript, Supabase Edge Function calling `gpt-5-nano` through the Responses API with a strict JSON schema.

## How I work

- Numbers in my READMEs come with the command that produces them. chilecompara's catalog counts carry the date they were measured and a five-run spread, because the number moves between passes and a single figure would imply it does not.
- pollagol-sim's out-of-domain backtest (n=5402, +0.044 points per match, 95% CI excludes zero) ran before the live season, not after.
- I default to local and reproducible where the domain allows it: chemtrace runs entirely on the user's machine, with emission factors in a JSON file, one entry per energy type with its source and year.

## Elsewhere

LinkedIn: [Sebastián Damiani Wolf](https://www.linkedin.com/in/sebasti%C3%A1n-damiani-wolf-753b95251)  
Essen, Germany.
