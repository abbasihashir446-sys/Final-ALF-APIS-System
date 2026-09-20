# AFL Assistant — Capstone (Week 3, Day 5)

A domain-locked chat and prediction assistant for AFL. It answers AFL questions, gives match win probabilities with a disclaimer, and refuses anything off-topic.

This project covers Tasks 1–5: hardening, evaluation, API + UI, monitoring plan, and executive report.

## Files

| File | What it is |
|---|---|
| `AFL_Capstone_Day5_Tasks_1_to_5.ipynb` | Main notebook. Run all cells top to bottom. |
| `AFL_Capstone_Day5_Tasks_1_to_5.pdf` | PDF copy of the notebook with outputs. |
| `afl_api.py` | FastAPI app (`/health`, `/chat`). Created by the notebook. |
| `streamlit_app.py` | Simple chat UI that calls the API. Created by the notebook. |
| `api_requirements.txt` | Python packages for the API and UI. |
| `results/` | Evaluation, monitoring and logging CSVs. |
| `EXECUTIVE_REPORT.txt` | Task 5 report. |
| `DEMO_SCRIPT_AND_SLIDES.txt` | 5–7 minute demo outline. |

## How to run

```bash
pip install pandas numpy jupyter
jupyter nbconvert --to notebook --execute AFL_Capstone_Day5_Tasks_1_to_5.ipynb
```

To try the API and UI:

```bash
pip install -r api_requirements.txt
uvicorn afl_api:app --reload        # terminal 1 → http://127.0.0.1:8000/docs
streamlit run streamlit_app.py      # terminal 2
```

## What each task does

1. **Hardening**: AFL-only guardrails, prompt-injection detection, repeated-abuse blocking, tool timeouts, a standard prediction disclaimer.
2. **Evaluation**: 32 test cases across factual Q&A, prediction sanity, scope guardrails and multi-turn coherence.
3. **API + UI**: FastAPI `/chat` endpoint, Streamlit front end, structured logging schema.
4. **Monitoring**: alert thresholds (latency, errors, leaks, drift) and a weekly data-refresh loop.
5. **Report**: executive summary and demo script.

## Current results

- Overall pass rate: **87.5%** (28 of 32 cases).
- Prompt-injection tests: **2 of 3** blocked.
- Weakest category: **Scope Guardrails (62.5%)**.

## Known limitations

- The API returns a **placeholder prediction** (55% / 45%) until the real Week 3 Day 4 LangGraph model is connected.
- The model vs ladder benchmark table is empty and needs real held-out results.
- The guardrails use keyword matching, so some off-topic and injection phrasings get through.
- No authentication or rate limiting yet, so it is not production-ready.


