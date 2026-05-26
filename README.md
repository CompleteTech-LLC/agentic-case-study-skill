# Agentic Case Study Skill

<p align="center">
  <img src="assets/logo.png" alt="CompleteTech LLC logo" width="260">
</p>

A CompleteTech LLC Codex skill for creating case studies, testimonials, and proof assets after agentic development delivery.

## About

Part of the CompleteTech LLC agentic services skill library. This skill packages verified delivery outcomes into approved proof assets while preserving confidentiality, attribution boundaries, and brand consistency.

## OpenClaw / ClawHub Metadata

- Skill key: `agentic-case-study-skill`
- Version-ready metadata: `1.0.0`
- Homepage: https://github.com/CompleteTech-LLC/agentic-case-study-skill
- README: https://github.com/CompleteTech-LLC/agentic-case-study-skill#readme
- Runtime binaries: `python3`
- Python packages: `reportlab>=4.0` (optional PNG preview: `pypdfium2`, `pillow`)
- Intended registry/discovery tags: `latest`, `complete-tech`, `codex-skill`, `agentic-development`, `agentic-workflows`, `case-study`, `testimonials`, `proof-assets`, `pdf`, `pdf-generator`
- License: repository code, templates, and documentation use MIT; ClawHub publishing is intentionally skipped for now.
- Brand assets: CompleteTech LLC names, logos, seals, and brand assets are reserved; see `BRAND_ASSETS.md`.

## Workflow Diagram

Source: [assets/diagrams/workflow.mmd](assets/diagrams/workflow.mmd).


```mermaid
flowchart LR
  A[Verified delivery evidence] --> B[Approval and attribution check]
  B --> C{Public use allowed?}
  C -->|No| D[Anonymized proof asset]
  C -->|Yes| E[Named case study or testimonial]
  D --> F[Sales, website, nurture, or portfolio reuse]
  E --> F
  classDef source fill:#eef6ff,stroke:#3778c2,color:#102a43;
  classDef gate fill:#fff7e6,stroke:#c97a12,color:#3d2600;
  classDef output fill:#eefaf0,stroke:#2f8f46,color:#12351d;
  class A source;
  class B,C gate;
  class D,E,F output;
```

## What It Does

- Selects the right proof artifact by evidence, approval status, and channel.
- Drafts case study intake, client interviews, anonymized/named case studies, before/after summaries, implementation stories, technical notes, risk/control summaries, testimonials, proof libraries, sales one-pagers, website case studies, LinkedIn posts, nurture stories, referral blurbs, portfolio entries, pitches, award submissions, press releases, and approval checklists.
- Helps turn delivered agentic workflow projects into credible sales and marketing assets without inventing proof or exposing sensitive details.
- Keeps proof aligned with practical CompleteTech LLC positioning: bounded agentic workflow implementation, human approval gates, evaluation, monitoring, documentation, support, and handoff.

## Contents

- `SKILL.md` - operating instructions and proof-asset selection guide.
- `references/proof-catalog.md` - reusable case study/testimonial/proof templates.
- `references/use-case-decision-table.md` - quick guide for choosing the right artifact.
- `references/proof-lifecycle.md` - flow from proof intake through approval and reuse.
- `references/proof-positioning.md` - CompleteTech LLC evidence and anonymization guardrails.
- `scripts/render_proof.py` - deterministic template listing and rendering helper.
- `scripts/render_pdf.py` - branded CompleteTech PDF generator (Markdown -> PDF + optional PNG preview).
- `requirements.txt` - Python dependencies for branded PDF rendering.

## Quick Start

```bash
python3 scripts/render_proof.py --list
python3 scripts/render_proof.py \
  --template anonymized-case-study \
  --var workflow="support triage" \
  --var before_state="manual queue review" \
  --var after_state="reviewed agent workflow with approval gates"
```

Rendered assets are drafts. Replace placeholders with verified, client-approved facts before public or external use.

## Example

![Customer Support Email Triage Agent preview](assets/examples/example.png)

Example files: [Markdown](assets/examples/example.md) · [PDF](assets/examples/example.pdf) · [DOCX](assets/examples/example.docx).

**Client case study: Northwind Trading Co. — Customer Support Email Triage Agent**

- Named, client-approved proof with measured outcomes from the pilot evaluation set.
- Separates measured outcomes (93.4% routing accuracy) from qualitative observations.
- Includes an approved customer quote and the safety controls behind the result.
- Uses only verified, approved facts — no invented ROI or permissions.

Generate it in one command (branded PDF + Markdown, like the contract skill):

```bash
pip install -r requirements.txt
python3 scripts/render_proof.py --template public-named-client-case-study \
  --out assets/examples/example.pdf --png assets/examples/example.png \
  --markdown-out assets/examples/example.md \
  --logo assets/logo.png --title "Customer Support Email Triage Agent" --doc-type "CLIENT CASE STUDY" \
  --subtitle "Northwind Trading Co. × CompleteTech LLC" --meta "CASE NO.=CASE-2026-007" --meta "DATE=2026-07-01"
```

The committed `example.{md,pdf,png}` use curated, realistic demonstration data for the Northwind Trading Co. support-triage pilot; pass `--var key=value` to fill template placeholders with your own facts.

## Brand Notes

Use careful evidence packaging. Distinguish measured outcomes from qualitative observations, protect confidential details, anonymize when needed, avoid regulated-use assurances, avoid legal claims, avoid fabricated ROI/savings metrics, and preserve the CompleteTech LLC emphasis on bounded implementation, human approval gates, evaluation, monitoring, documentation, support, and handoff.

## License

Code, templates, and documentation are licensed under the MIT License. CompleteTech LLC names, logos, seals, and brand assets are reserved and are not licensed for reuse except to identify this project. See `LICENSE` and `BRAND_ASSETS.md`.

## Certificate Receipts

This skill can run normally without a classroom key. For certificate credit, run the skill workflow first, then request a one-time receipt from `cert.complete.tech`:

```bash
python scripts/request_receipt.py \
  --class-id "cls_agentic_case_study_skill" \
  --session-id "ses_YYYYMMDD_agentic_case_study_skill" \
  --completion-key "$CT_CERT_COMPLETION_KEY"
```

The helper sends `class_id`, `session_id`, `completion_key`, `skill_id`, `skill_version`, a generated `run_id`, optional artifact hash, and metadata to `https://cert.complete.tech/api/skill-runs`. It prints the receipt code and writes a receipt JSON file. Students use the receipt code at `https://cert.complete.tech/claim`. Do not commit real completion keys.

If the skill produced a file, include it so the receipt records an artifact hash:

```bash
python scripts/request_receipt.py --artifact output/example.pdf
```

### Receipt Tests

```bash
python tests/test_receipt_cli.py
```

The test uses a local fake receipt API and does not require live keys or the live `cert.complete.tech` endpoint.
