# FL-05 — Agent Concepts and MCP Basics
**General AI Fluency Explainer**

---

### Metadata
- **Author**: Muhammad Zayan
- **Track**: General AI Fluency
- **Assignment ID**: FL-05 (Agent Concepts and MCP Basics)
- **Module / Phase**: Build (core) — Week 4
- **Date**: August 2026

---

## 1. AI Workflows vs. AI Agents

An AI workflow is a structured, deterministic pipeline of operations where the sequence of steps and handoffs is hardcoded by a human developer. Each step has fixed inputs and outputs, and the system follows a set execution path without deciding its own actions. In contrast, an AI agent is an autonomous system that uses a Large Language Model (LLM) as its central decision-maker. Given a high-level goal and access to tools, the agent dynamically decides which actions to take, evaluates the results, handles errors, and loops until the goal is achieved.

The key difference lies in autonomy and dynamic routing. A workflow has a rigid, human-designed topology, whereas an agent has a self-directed feedback loop. My FL-04 Draft-Critique-Revise pipeline is classified as an AI workflow. It operates in a strict, hardcoded sequence: Step 1 (Draft), Step 2 (Critique), Step 3 (Revise), and Step 4 (Final Check). The model cannot decide to skip a step, loop back if a critique fails, or call external search tools. It simply processes the input through a fixed multi-prompt chain.

---

## 2. Model Context Protocol (MCP)

Model Context Protocol (MCP) is an open-standard protocol developed by Anthropic that defines a secure, standardized way for LLM applications (clients) to connect to external data sources, tools, and services (servers). Without MCP, developers must write custom, ad-hoc integrations for every tool or API they want an LLM to use. MCP standardizes this interface, enabling any compliant model to instantly discover and use tools or inspect resources, breaking model isolation.

The protocol is built around three core primitives: Tools, Resources, and Prompts. Tools are executable actions the model can trigger to perform side effects or retrieve dynamic data (e.g., writing a file or running a terminal command). Resources are read-only data contexts exposed by the server that the model can inspect for context (e.g., log files, database schemas, local configurations). Prompts are standardized templates served by the server to guide the model's behavior for specific tasks.

---

## 3. My FL-04 Pipeline

The FL-04 pipeline automates the drafting and polishing of internship documentation to ensure factual accuracy and eliminate AI fluff. In Step 1 (Draft), the system receives raw notes and produces a structured technical first draft. In Step 2 (Critique), the system receives the draft and outputs an 8-point critique of factual, structural, and stylistic issues. In Step 3 (Revise), the system receives the first draft and critique and produces a revised version. In Step 4 (Final Check), the system receives the revised draft and runs a 5-point quality assurance checklist to output the final verified draft.

Although this pipeline automates the editing process, human review is always required at the end to check metrics (such as row counts or column gotchas) before final submission. It currently qualifies as a workflow because it runs along a fixed, non-branching path with no tool access or self-correction loops.

---

## 4. Turning the Pipeline into an Agent

To upgrade this pipeline into an agent, I would introduce an autonomous verification loop with tool access. Instead of a static chain, the agent would be given a high-level goal: "Refine these raw notes and verify all claims against the repository code." The agent would first read the raw notes. It would then use a file-system search tool (like grep_search) to search the repository for referenced variables (e.g., is_declining_label or impressions_90d) to confirm they exist and match the code. If a discrepancy is found, it would automatically rewrite the draft to correct the error, inspecting its own output and repeating the check until all claims are verified before writing the final document to the workspace.

---

## 5. MCP in My Work

Under my current internship context, an MCP connection could allow Claude to perform three realistic tasks that plain chat cannot: First, an SQL/DuckDB MCP server could allow Claude to query the active database schema to verify that the columns and types in a drafted data contract match the actual warehouse schema. Second, a file-system MCP tool could allow Claude to directly read and write python cells inside work/notebooks/w04_baseline_score.ipynb to debug code blocks on-demand. Third, a shell-execution MCP tool could allow Claude to run Python test scripts in the repository background to verify that a code refactoring didn't break baseline scoring rules, inspecting the test logs directly.

---

## 6. Connector / MCP Evidence

The table below lists the MCP / connector tools available in the workspace environment, detailing what they accessed/did and their verification status based on actual execution logs in this session.

| Task | Connector/MCP | What the tool accessed/did | Evidence status |
| :--- | :--- | :--- | :--- |
| **Repository File Read** | `default_api:view_file` | Read the contents of `skills/README.md` and `FL-04` markdown walkthrough files. | **Verified** |
| **Local Script Execution** | `default_api:run_command` | Ran python validation scripts to check document word counts and compile Docx. | **Verified** |
| **Canvas UI Design Objects** | `StitchMCP:list_projects` | Standard MCP tool configured for canvas UI management. | **Not verified** (Not run in session) |

---

## 7. Reflection

Developing a deterministic workflow and comparing it with autonomous agents highlighted the value of structured execution paths. While workflows provide consistency and safety, they struggle with unexpected edge cases or errors. Enabling an LLM to utilize Model Context Protocol (MCP) tools bridges the gap between passive chat and active system execution. When a model can inspect its workspace and run shell tests, it transitions from a text synthesizer into a proactive contributor that validates its own output against reality.

---

## Evidence Checklist

Before final submission of FL-05, ensure:
- [x] Explainer word count is between 600 and 900 words (verified at 687 words).
- [x] Only genuine default_api calls used in this session are marked as "Verified" (no StitchMCP tools were executed).
- [x] Walkthrough MD and DOCX files are compiled and saved in the repository root directory.
