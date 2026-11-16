# Frozen submission · team HSA Connection

- **Frozen on:** 2026-11-06, agreed with the team. Switching costs revised on 2026-11-16 (robust choice over possession definitions, notebook 04 section 4).
- **File:** `HSA_Connection.csv` (199,319 frames, `frame,label`), SHA-256 `ce099b852b8cfd85550de359ed837407642a559b2ec1e3364d08cf50d5a054ae`, checked with the official validator.
- **Model description:** `frozen_model.json`, SHA-256 `9d31956a3d92abb4a3e926ecf491e013dcad27062a82ed8a026a4b7dceb14332`.
- **Created by:** `notebooks/04_submission.ipynb`, run order 01 → 02 → 03 → 04. A full run from the raw data reproduces the submission file bit for bit.

## Model

- D model: boosting on base, multi-scale and possession features (159 features).
- H model: boosting on possession features and robust team shape (59 features).
- Decoder: joint Viterbi with c_HA = 20, c_D = 40, then kick snap, kick-off rule and restart prior (w = 4).
- Trained on 7 DFL matches (degraded, d67s) and 3 Metrica sample matches.

## External validation (spellF1, leave-one-match-out over 10 matches)

| | Metrica (main criterion) | DFL d67s |
|---|---:|---:|
| Submission | 0.634 | 0.478 |
| Submission, controlled possession (touches < 3 s do not count) | 0.756 | 0.591 |
| Baseline smooth50 | 0.405 | 0.214 |

The public 5-minute ground truth did not influence any decision.
