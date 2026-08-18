# FL-03 — Consistency, Not Talent

## 1. Visual Identity

Documenting the actual visual choices used in my portfolio and technical deliverables across the workspace:

- **Color System**:
  - **Primary Accent (`#1F4E79` / `#1B365D`)**: Deep Navy Blue used for primary headings, hero branding, and primary action CTAs. Establishes a professional, enterprise-grade engineering feel.
  - **Secondary Accent (`#4A5568` / `#008080`)**: Muted Slate Grey and Deep Teal used for secondary section subtitles, metadata tags, and table header accents to establish a clear visual hierarchy.
  - **Neutral Backgrounds (`#FFFFFF` / `#F9FAFB` / `#F7FAFC`)**: Clean off-white and soft grey backdrops for main content containers and metadata callout boxes, maximizing contrast without harshness.
  - **Text & Body Copy (`#262626` / `#333333`)**: Off-black for body text, avoiding standard pure black (`#000000`) to prevent eye fatigue during long technical reads.
  - **Code & Dark Blocks (`#1A202C` / `#F2F4F7`)**: Dark Slate for code block backgrounds and clean light grey for inline code snippets.

- **Typography**:
  - **Primary Headings (`Arial` / `Inter` / `Calibri Bold`)**: Clean, high-legibility sans-serif set at distinct sizes (Title: 22–24pt, H1: 15–16pt bold, H2: 12–13pt bold) to guide recruiters cleanly through project structures.
  - **Body Copy (`Calibri` / `Inter`)**: Set at 10.5–11pt (16px equivalent) with 1.15–1.5 line-spacing to ensure long-form technical case studies are easy to read and scan.
  - **Monospace / Technical Code (`Consolas` / `Fira Code`)**: Set at 9pt for terminal outputs, SQL schemas, python code blocks, and feature parameter matrices.

- **Spacing / Layout**:
  - **Grid & Margins**: Strict 8px spacing grid (8px, 16px, 24px, 32px margins/padding) with standardized 1-inch (72pt) page margins on documents and centered container max-widths on web layouts.
  - **Section Dividers**: Subtle border rules (`1px solid #E2E8F0`) and 12–16pt paragraph spacing after major section headings to maintain consistent vertical rhythm.

- **Components**:
  - **Primary Buttons / CTAs**: Solid Navy (`#1F4E79`) background with bold white text (`#FFFFFF`) for main actions (*"View My Work"*, *"Contact Me About Opportunities"*).
  - **Secondary Buttons / Links**: Outlined buttons (`1px solid #1F4E79`) with Navy text for secondary navigation actions (*"GitHub Repo"*, *"Download Case Study"*).
  - **Cards & Callout Boxes**: Light rounded containers (`#F7FAFC` / `#F0F4F8`) featuring a 2–3px primary accent left border (`#1B365D`) for key takeaways, dataset gotchas, and executive summaries.
  - **Navigation**: Clean, sticky top header bar with clear text anchors (Home, Projects, About, Contact).

- **Background / Visual Treatment**:
  - Minimalist, distraction-free neutral canvas. Eliminates glowing background animations, heavy drop shadows, or loud decorative imagery so the technical proof remains the central focus.

---

## 2. Design Principles

The overarching design philosophy for this portfolio is **Frame, Not Upstage**:

1. **The Visual System is a Stage**: The interface exists solely to highlight the machine learning work, problem framing, and engineering decision-making. Excessive visual decorations distract recruiters from reading case studies.
2. **Scannability First**: Recruiters review portfolios in 30–60 seconds. High-contrast typography hierarchy, bold lead-ins, bulleted decision points, and clean tables allow them to quickly evaluate technical depth.
3. **Evidence Over Decoration**: Real project artifacts (execution screenshots, SVG feature importances, evaluation tables) replace decorative stock illustrations.
4. **Predictable Consistency**: Every section (SentinelOps, GitVerse, VisionForge, FlyRank Internship) follows an identical structural template: *Problem → Work → Key Decisions → Technical Details → Measured Outcome*.

---

## 3. Image Decisions

The portfolio relies strictly on authentic technical evidence rather than generic decorative graphics:

- **FL-04 Workflow Execution Screenshots (`submission/fl04_screenshots/fl04_workflow_step_01.png` to `11.png`)**:
  - **Where Used**: FL-04 Automation Workflow case study and project submission appendix.
  - **Why Selected**: Captures the exact Claude Projects 4-step pipeline (Draft → Critique → Revise → Final Check) in action.
  - **Type**: Real project execution asset (100% authentic screenshots).
  - **Why It Supports the Work**: Proves that the no-code multi-step prompt workflow was actually built, executed, and verified against an 8-point critique rubric.

- **Baseline & Model Feature Importance SVG Charts (`outputs/charts/top_feature_importance.svg`, `trend_distribution.svg`, `action_mix.svg`)**:
  - **Where Used**: ML-07 Baseline Action Score review and ML-08 Capstone Model case study sections.
  - **Why Selected**: Visualizes the exact feature importance rankings (`days_with_impressions`, `log_impressions_90d`, `avg_position`) and label distribution derived from the 30,000 Hugging Face warehouse dataset rows.
  - **Type**: Real pipeline output asset (generated via `scripts/02_baseline_score.py` and `w05_model.ipynb`).
  - **Why It Supports the Work**: Demonstrates data-driven validation and empirical ML methodology rather than theoretical claims.

- **FlyRank Refresh Model Results PDF Report (`outputs/flyrank_refresh_model_results.pdf`)**:
  - **Where Used**: FlyRank Internship case study downloads and evidence appendix.
  - **Why Selected**: Standard automated PDF summary generated by the reference pipeline evaluating model precision vs baseline.
  - **Type**: Real generated pipeline artifact.
  - **Why It Supports the Work**: Serves as downloadable verification of model performance metrics (`Precision@50 = 0.6800` vs `0.2400` baseline).

---

## 4. Rejected Visuals / Judgment

To maintain strict professional alignment and prevent visual distraction, the following visual choices were explicitly rejected:

1. **Rejected Choice 1: AI-Generated Futuristic Tech Illustrations**:
   - *What was rejected*: Glowing floating brains, abstract AI network webs, or stock futuristic cyberpunk banners.
   - *Why rejected*: Generic AI stock imagery adds zero proof value and signals style over substance. Real terminal screenshots and SVG charts provide genuine evidence of technical execution.

2. **Rejected Choice 2: High-Saturation Neon Gradients (Dark Mode Violet/Pink)**:
   - *What was rejected*: Trendy bright neon accent colors (`#FF00FF`, `#00FFFF`) on pitch-black backgrounds.
   - *Why rejected*: Extreme visual contrast causes severe eye fatigue when reading long technical case studies and appears un-calibrated for corporate ML engineering roles.

3. **Rejected Choice 3: Complex Scroll-Triggered Parallax & Canvas Animations**:
   - *What was rejected*: Heavy 3D card tilt effects, particle canvas backgrounds, and scroll-jacking transitions.
   - *Why rejected*: Interactive visual gimmicks slow down page load times, degrade mobile usability, and distract reviewers from reading core engineering decisions and metrics.

---

## 5. Final Visual Identity Summary

The resulting visual identity is a clean, enterprise-grade, evidence-first design system. Built on a refined palette of Deep Navy (`#1F4E79`), Muted Slate (`#4A5568`), and crisp neutral backdrops (`#F9FAFB`), it prioritizes scannability, structural consistency, and legibility. By framing real project artifacts—such as actual terminal execution logs, SVG feature importance charts, and structured model evaluation tables—the visual design quietly steps back to let the technical quality of the machine learning and AI fluency work speak for itself.
