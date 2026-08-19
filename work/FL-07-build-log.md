# FL-07 — Agent Build Log

## 1. What I Started With
- **Design Specification**: `FL-06-Personal-Agent-Design.md` detailing the Search Intelligence & Research Agent (SIRA), its closed-loop architecture (`Plan → Act → Observe → Evaluate`), 5 proposed tools, and 5 evaluation test cases.
- **Skill Router Framework**: `skills/README.md` defining focused single-task instructions to prevent context bloat.
- **Repository Infrastructure**: Existing Python scripts in `scripts/` (`03_train_model.py`, `ml_utils.py`), execution artifacts in `outputs/` (`model_results.json`), notebooks in `work/notebooks/` (`w05_model.ipynb`), and `submission/paper_url.txt`.

---

## 2. What Broke & Challenges Encountered
- **Path Resolution Errors**: Initial script iterations used relative file path strings (`"outputs/model_results.json"`), which failed with `FileNotFoundError` when executing `sira_agent.py` from different working directories.
- **Placeholder URL Edge Case**: Naive string checks on `submission/paper_url.txt` initially treated the placeholder text (`PASTE-YOUR-DEPLOYED-PAPER-URL-HERE`) as an active URL.

---

## 3. What I Changed
- **Repository Root Anchoring**: Updated `SIRAAgentMVP` to dynamically anchor all file paths against `REPO_ROOT = Path(__file__).resolve().parent.parent`, enabling reliable execution from any workspace location.
- **Strict Protocol Validation**: Implemented explicit string pattern checks (`url_line.startswith("https://")`) in the deployment verifier, logging an explicit uncertainty disclosure when the placeholder is active.

---

## 4. What Worked
- **Autonomous Read-Only Loop**: Successfully implemented the 4-step **Plan → Act → Observe → Evaluate** execution cycle without requiring any manual user interventions during the run.
- **Empirical Artifact Verification**: Accurately parsed `outputs/model_results.json` to extract model selection (`random_forest`), validation strategy (`client_holdout`), test row count (`2,325`), model `Precision@50` (`0.6800`), baseline `Precision@50` (`0.2400`), and calculated out-of-sample performance lift (**2.83x lift**).
- **Feature Safety & Leakage Guard**: Audited `work/notebooks/w05_model.ipynb` to verify zero inclusion of target-derived features (`trend_pct`, `trend_direction`).
- **Audit Logging**: Maintained an execution log capturing tool actions, targets, status codes, and file byte sizes.

---

## 5. What I Cut from the FL-06 Specification
- Cut live DuckDB Hugging Face remote Parquet querying (`mcp_duckdb`).
- Cut automated Git staging, committing, and pushing (`git_commit`).
- Cut autonomous code editing and refactoring tools (`replace_file_content`).
- Cut interactive multi-turn chat UI menus.

---

## 6. Why I Cut It
- **MVP Scope Constraint**: FL-07 requires building the smallest working MVP that completes one end-to-end task without mid-run manual edits or overengineering.
- **Safety Guardrail Compliance**: FL-06 guardrails strictly require human-in-the-loop approval before performing mutating side-effects (git push, disk edits).
- **Sufficiency of Local Artifacts**: Inspecting committed JSON metrics (`outputs/model_results.json`) and notebooks provided 100% of the evidence required to verify model performance and data contracts without needing external DuckDB server connections.

---

## 7. Final MVP Capabilities
- Receives verification requests via command-line interface (`python scripts/sira_agent.py --query "..."`).
- Programmatically inspects workspace files using `tool_read_file` and `tool_grep_search`.
- Verifies model parameters, evaluation metrics, feature safety, and deployment statuses.
- Generates structured markdown verification reports with exact file citations, metric lifts, tool audit logs, and explicit uncertainty disclosures.

---

## 8. Known Limitations
- **Read-Only Scope**: Cannot execute code mutations or retrain models dynamically.
- **Pre-defined Verification Paths**: Currently tuned to audit repository paths (`outputs/`, `work/notebooks/`, `submission/`).
- **Local File Dependency**: Operates on local repository artifacts rather than querying remote Hugging Face tables over live HTTP.
