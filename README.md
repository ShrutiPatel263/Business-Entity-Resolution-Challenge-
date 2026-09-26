# Business-Entity-Resolution-Challenge-

## Pipeline : 

                  ┌──────────────────┐
                  │   Source 1       │
                  │ Reference DB     │
                  └────────┬─────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Data Cleaning /    │
                 │ Normalization      │
                 └────────┬───────────┘
                          │
                          ▼
                 ┌────────────────────┐
                 │ Candidate Blocking │
                 │                    │
                 │ Name + Address +   │
                 │ Country + Tokens   │
                 └────────┬───────────┘
                          │
                          ▼
             ┌─────────────────────────────┐
             │ Candidate Pairs             │
             │                             │
             │ S1 ↔ S2                    │
             │ S1 ↔ S3                    │
             └─────────────┬───────────────┘
                           │
                           ▼
                ┌────────────────────┐
                │ Feature Engineering│
                │                    │
                │ name similarity    │
                │ address similarity │
                │ token similarity   │
                │ country equality   │
                │ char TF-IDF        │
                └─────────┬──────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Pair Classifier  │
                 │                  │
                 │ LightGBM /       │
                 │ XGBoost /        │
                 │ Logistic Reg.    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Threshold +      │
                 │ Singleton Logic  │
                 └────────┬─────────┘
                          │
                          ▼
             ┌─────────────────────────┐
             │ matching_results.tsv   │
             │ candidate_pairs.tsv    │
             └─────────────────────────┘


