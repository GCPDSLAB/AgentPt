# Feature: siglas-definiciones-hover

Add inline definitions ("define before using") and hover tooltips for the acronyms/siglas
in the AgentPt deck and its companion docs, without changing any content meaning.

- Feature doc: `odd/tasks/siglas-definiciones-hover.md`
- Engram mirror: `odd/siglas-definiciones-hover/tasks/tasks.md`
- Status: PLAN (frozen for judgment day)

---

## 1. Plan (frozen target for Judgment Day)

### 1.1 Goals

1. **Define before using**: each target sigla is expanded inline at its first occurrence
   per slide unit in `index.html` (e.g. `Spec-Driven Development (SDD)`), and similarly at
   first use per document in `README.md` and `demos/*.md`.
2. **Hover everywhere**: every occurrence of every sigla in the inventory gets a hover
   with its definition — in the HTML text layer, inside SVG diagrams, and in Markdown docs.
3. Nothing else changes: no content rewording, no layout changes, no new files committed
   unless required by the verification protocol.

### 1.2 Decisions (user-confirmed)

| Decision | Choice |
|---|---|
| Hover mechanism | Semantic `<abbr title="…">` + dotted underline CSS affordance |
| "Define before using" granularity | First use **per slide unit** (deck) and first use **per document** (README, demos); hover always available |
| SVG diagrams | **USER OVERRIDE (2026-XX-XX, post-approval): NOT included.** Diagrams reverted to original; hover applies to the text layer only. Original decision (nested SVG `<title>`) was implemented, then reverted at the user's request (“revert the diagrams to the original and only add the hover to the text”). Remaining scope: HTML text layer + Markdown prose. |
| Definition language | English canonical term + short Spanish gloss in the tooltip; inline expansion shows the English term + sigla in parentheses |

### 1.3 Canonical definitions table (single source of truth)

Both judges and the executor use exactly this table. **User-facing format (language policy §1.2):**
Tooltip text = `English canonical (Spanish gloss)` (for Spanish siglas like IA, the gloss itself is the expansion).
Inline expansion text = `English canonical (SIGLA)`. The **Tooltip** and **Inline** columns are final
user-facing copy — paste verbatim; no meta-labels, no ⚠ notes (JD-PLAN-003/S3 fix). The **Executor data**
column is agent-facing only (scope, exclusions, epistemic flags) and must never leak into user-facing strings.
`—` in Inline = no inline expansion (hover-only).

**Target set — inline define-before-use + hover:**

| Sigla | Tooltip (final copy) | Inline (final copy) | Executor data |
|---|---|---|---|
| SDD | Spec-Driven Development (desarrollo guiado por especificaciones) | Spec-Driven Development (SDD) | First visible-text use per slide: 12 ("(SDD)"); 14 ("SDD o TDD", SVG-only — no inline there); per doc: demos/04 (title hover-only, first body occurrence carries inline). |
| ODD | Organic Driven Development (desarrollo orgánico guiado) | Organic Driven Development (ODD) | Only slide 21 ("OpenSpec, SDD y ODD" ×2, text + SVG); hover everywhere. |
| TDD | Test-Driven Development (desarrollo dirigido por pruebas) | Test-Driven Development (TDD) | SVG-only (slide 14); per-slide inline not applicable (documented deviation). |
| PRD | Product Requirements Document (documento de requisitos de producto) | Product Requirements Document (PRD) | Slides 15–18, 20 (text); README module 5 row (prose). |
| CI-CD | Continuous Integration / Continuous Delivery (integración continua y entrega continua) | Continuous Integration / Continuous Delivery (CI-CD) | Slide 1 only (text "…DevOps con CI-CD.", SVG "DevOps · CI-CD"); deck writes "CI-CD" (one hover unit, not "CI/CD"). |
| DORA | DevOps Research and Assessment (investigación y evaluación de DevOps (Google Cloud)) | DevOps Research and Assessment (DORA) | First per-slide text use on 8–10 ("(DORA, 2025)"); slide 22 references ("DORA: State of…", "Google Cloud / DORA"). |
| QA | Quality Assurance (aseguramiento de calidad) | Quality Assurance (QA) | SVG-only (slide 1 "Pruebas / QA"); per-slide inline not applicable (documented deviation). |
| PO | Product Owner (dueño del producto) | Product Owner (PO) | Slide 4 (text + SVG); README module 2 row (prose). |
| UX | User Experience (experiencia de usuario) | User Experience (UX) | Slides 15–17; first use on slide 15 is inside an SVG `<text>` label — no inline there; visible-text uses from slide 16; `\bUX\b` must not match inside "UX-DR" (§1.6). |
| MCP | Model Context Protocol (protocolo de contexto del modelo) | Model Context Protocol (MCP) | Slide 21 only (text "…vía MCP o API…", SVG "MCP / API"). |
| API | Application Programming Interface (interfaz de programación de aplicaciones) | Application Programming Interface (API) | Slide 7 (tarifas de API, text + SVG) and slide 21 (text + SVG). |
| BYOK | Bring Your Own Key (trae tu propia llave (de API)) | Bring Your Own Key (BYOK) | SVG-only (slide 7 "+75 proveedores (BYOK)"); per-slide inline not applicable (documented deviation). |
| DevOps | Development + Operations (desarrollo y operaciones) | Development + Operations (DevOps) | Slide 1 (text + SVG) and slide 21 ("El ciclo DevOps, orquestado"); exclusion: "Azure DevOps" whole token, never wrapped (§1.6). |
| SPEC-WEAVER | Stack de especificaciones del deck que teje cada etapa del ciclo con su herramienta ('SPEC' = especificaciones, 'WEAVER' = tejedor) | SPEC-WEAVER | No English expansion exists: the canonical is the stack's proposed name, so inline stays the sigla itself. Case variant "SpecWeaver" → same tooltip; "UN-SpecWeaver" → whole token (§1.6). |
| SDLC | Software Development Life Cycle (ciclo de vida del desarrollo de software) | Software Development Life Cycle (SDLC) | README only ×2. Current first use is a Spanish partial expansion ("del desarrollo de software (SDLC)") — definition-only insertion authorized to reach the locked format (§1.6, B-S1). |
| PR | Pull Request (solicitud de cambios para revisión) | Pull Request (PR) | Slide 21 only ("GitHub PR", SVG) — per-slide inline not applicable there (deviation); `\bPR\b` must not match inside "PRD"/"SWEPR". |
| MR | Merge Request (solicitud de fusión (terminología de GitLab)) | Merge Request (MR) | Slide 21 only ("GitLab MR", SVG) — per-slide inline not applicable there (deviation). |
| DAG | Directed Acyclic Graph (grafo acíclico dirigido) | Directed Acyclic Graph (DAG) | demos/04 only (line 44, prose). |
| LLM | Large Language Model (modelo de lenguaje grande) | Large Language Model (LLM) | Added in Round-1 fix (ledger A8/B-F7c): singular "LLM" in demos/04 line 14 (prose). Plural "LLMs" → hover-only row. |

**Hover-only inventory (definition on hover, no inline expansion):**

| Sigla | Tooltip (final copy) | Inline (final copy) | Executor data |
|---|---|---|---|
| IA | Inteligencia Artificial | — | Spanish sigla: no English canonical — the tooltip is the expansion. Occurrences: cover title, slides 2–3, 5, 8–11, 13, footer running-title; README ×6; demos/01 ×2 (prose); demos/02 ×1 (inside ```prompt fence — excluded). No inline anywhere. |
| AI | Artificial Intelligence (inteligencia artificial) | — | Standalone uses only; product names excluded (OpenAI, Moonshot AI, Zhipu AI, GenAI). Slide 7: every "AI" is inside a product name → exclusion-only there. Slide 22: ×6 standalone (reference prose). |
| UNAL | Universidad Nacional de Colombia (universidad pública colombiana) | — | Cover/footer img alt attributes (listing only, not wrapped) + footer running-title "DIEEC-UNAL-Manizales."; `\bUN\b` must not match inside "UNAL". |
| LIA / labIA | Laboratorio de Inteligencia Artificial (laboratorio del grupo (sede Manizales)) | — | No visible-text occurrence (only img filename "logo_labIA.png" and spelled-out alt); protective roster entry; case variant "labIA" matched case-sensitively. |
| DIEEC | Departamento de Ingeniería Electrónica y de Computadores (UNAL Manizales) — expansión no publicada en el repositorio (inferida) | — | Expansion inferred, not published in the repo; sole occurrence: footer running-title "DIEEC-UNAL-Manizales.". |
| UN | Universidad Nacional | — | Not expanded in the repo (same epistemic status as DIEEC/GCPDSLAB). Whole-token rule: "UN" is wrapped ONLY inside the token "UN-SpecWeaver" (rail button, slide-21 kicker, README module 6); the slide-13 SVG "DE PEDIR Y REZAR A UN PROCESO" is the Spanish article — never wrapped (§1.6/S2). |
| GCPDSLAB | Organización de GitHub del laboratorio — expansión no publicada en el repositorio | — | GitHub org handle; expansion not published. Sole occurrence: clone URL inside a ```bash fence in README — fenced, excluded from wrapping. |
| SWE-bench | Software Engineering Benchmark (punto de referencia de ingeniería de software) | — | Slide 7 ("SWE-bench Verified") and slide 22 (prose reference); only the "SWE-bench" token is wrapped. |
| SWEPR | Stanford Software Engineering Productivity Research (investigación de productividad en ingeniería de software (Stanford)) | — | Slide 9 ("Stanford SWEPR"); slide 22 cites the spelled-out name (no token); `\bPR\b` must not match inside "SWEPR". |
| METR | Model Evaluation and Threat Research (evaluación e investigación de modelos) | — | Slide 9 (SVG label) and slide 22 ×1 ("…productivity. METR."). |
| NIST | National Institute of Standards and Technology (Instituto Nacional de Estándares y Tecnología (EE. UU.)) | — | Slide 5 only ("(NIST, 2023)"). |
| MIT | Massachusetts Institute of Technology (institución que da nombre a la licencia MIT) | — | Slide 7 only (prose "licencia MIT", SVG "MIT · off-peak"). |
| LLMs | Large Language Models (modelos de lenguaje grandes) | — | Wraps the plural form "LLMs" (slide 22: "reasoning in LLMs"); singular "LLM" → target-set row. |
| GPT | Generative Pre-trained Transformer (transformador preentrenado generativo) | — | Slide 7 only: wrap only the "GPT" prefix in "GPT-6 Astra"; "Astra" is not wrapped. |
| GLM | General Language Model (modelo de lenguaje general (serie de Zhipu AI)) | — | Slide 7 only ("DeepSeek · Qwen · Kimi · GLM"); "Zhipu AI" is a product name (no hover on "AI"). |
| MoE | Mixture of Experts (mezcla de expertos) | — | Slide 7 only (SVG "2,8T MoE"). |
| GH | GitHub (plataforma de desarrollo colaborativa) | — | Slide 21 only ("GH Actions", SVG); the full name "GitHub" is a product name (no hover). |
| AWS | Amazon Web Services (servicios web de Amazon) | — | demos/04 line 27 only (inside ```prompt fence — excluded); no deck/README occurrence. |
| GCP | Google Cloud Platform (plataforma en la nube de Google) | — | demos/04 line 27 only (inside ```prompt fence — excluded); no deck/README occurrence. |
| HTML | HyperText Markup Language (lenguaje de marcado de hipertexto) | — | README (prose); demos/04 line 60 (prose) + line 27 (fence — excluded). |
| CSS | Cascading Style Sheets (hojas de estilo en cascada) | — | README (prose); demos/02 ×2 (prose); demos/04 line 60 (prose) + line 27 (fence — excluded). |
| JS | JavaScript (lenguaje de programación del navegador) | — | README (prose); demos/02 ×2 (prose); demos/04 line 60 (prose) + line 27 (fence — excluded). |
| CLI | Command-Line Interface (interfaz de línea de comandos) | — | demos/01 ×2 (prose, "desde el CLI", "CLI propia"). |
| FTS5 | Full-Text Search version 5 (búsqueda de texto completo versión 5 (SQLite)) | — | demos/01 only (prose "SQLite con FTS5 (full-text search nativo)"); "SQLite" itself is a product name (no hover). |

### 1.4 Placement map (where each sigla actually occurs)

Re-verified against the repo in Round 1 (JD-PLAN-001 fix). `index.html` has **23 `<article class="slide">` units**:
cover (data-index 0) + slides 1–21 (data-index 1–21) + the `is-wide` "23 · Fuentes" article (data-index 22),
plus global chrome.

| Location | Siglas present (verified) |
|---|---|
| Slide 1 | QA (SVG), DevOps (text + SVG), CI-CD ×2 (text + SVG) |
| Slide 2–3 | IA |
| Slide 4 | PO (text + SVG) |
| Slide 5 | IA, NIST |
| Slide 7 | API, BYOK (SVG), SWE-bench, MIT, GPT, GLM, MoE — "AI" exclusion-only (every occurrence is inside OpenAI / "Moonshot AI") |
| Slide 8–10 | DORA, IA |
| Slide 9 | SWEPR, METR |
| Slide 11 | IA |
| Slide 12 | SDD |
| Slide 13 | IA; "UN" solo como artículo español en el SVG "DE PEDIR Y REZAR A UN PROCESO" — nunca se envuelve (§1.6) |
| Slide 14 | SDD, TDD (SVG) |
| Slide 15–17 | PRD, UX (primer uso de UX en el slide 15 dentro de texto SVG "arquitectura y UX"; texto visible desde el slide 16; "UX-DR" excluido) |
| Slide 18 | PRD |
| Slide 20 | PRD, SPEC-WEAVER |
| Slide 21 | SPEC-WEAVER, DevOps, MCP, SDD, ODD, API, PR (SVG), MR (SVG), GH (SVG); Azure como nombre de producto excluido ("Azure DevOps" ×2, "Azure Boards"); "UN" solo dentro del kicker "22 &middot; UN-SpecWeaver" (token completo) |
| Slide 22 (Fuentes, is-wide, data-index 22) | AI ×6, DORA ×2, METR ×1, LLMs ×1, SWE-bench ×1 — todas en prosa de referencias; "GenAI" (Veracode) = término compuesto, excluido; sin IA independiente dentro del artículo (el ledger S1 lista "IA (heading)": no corroborado — véase nota Round-1 en §4) |
| Cover | IA (título "Agentes de IA…"); UNAL (img alt "Laboratorio de Inteligencia Artificial UNAL" — atributo, no se envuelve) |
| Global chrome (rail, kicker, footer) | "UN-SpecWeaver": botón del rail "6. UN-SpecWeaver" y kicker "22 &middot; UN-SpecWeaver" (token completo, tooltip SPEC-WEAVER); running-title del footer: IA ("Agentes de IA… Propuesta.") + DIEEC y UNAL ("DIEEC-UNAL-Manizales.") — hover-only |
| README.md | SDLC ×2, IA ×6, HTML, CSS, JS, PO, PRD, SPEC-WEAVER, "UN-SpecWeaver" (token completo, módulo 6); GCPDSLAB dentro de bloque ```bash (fenced — excluido) |
| demos/01-engram.md | IA ×2, CLI ×2, SQLite (label, nombre de producto), FTS5 |
| demos/02-agentes-paralelos.md | JS ×2, CSS ×2 (prosa); IA ×1 y SDD ×1 dentro de bloque ```prompt (fenced — excluidos) |
| demos/03-skills.md | — (ninguna sigla del inventario) |
| demos/04-sdd.md | SDD (título hover-only; primer uso en cuerpo ⇒ expansión inline), LLM ×1 (singular, prosa), DAG ×1 (prosa), HTML/CSS/JS (prosa en línea 60; línea 27 dentro de bloque ```prompt — excluida), AWS ×1, GCP ×1 (línea 27, fence — excluidos) |

**Special cases (verified):**
- CI/CD is written as **"CI-CD"** in the deck (not "CI/CD") — one hover unit with the joint definition.
- SDLC appears only in `README.md`; DAG only in `demos/04-sdd.md`; neither exists in `index.html`.
- QA, BYOK, TDD (and, on slide 21, PR and MR) appear **only inside SVG diagrams** — they get SVG hover; the per-slide inline
  expansion requirement cannot be met in visible text for these, so the SVG `<title>` carries
  the definition (documented deviation; no visible expansion inside diagrams by decision 1.2). "GH Actions" is
  likewise SVG-only (GH is hover-only anyway).
- "AI" inside product names (e.g. "Moonshot AI", "OpenAI") is excluded (see 1.6); on slide 7 every "AI" occurrence
  is inside a product name → exclusion-only there.
- **"Azure DevOps"** (3+ occurrences, text + SVG on slide 21) and **"Azure Boards"** are product names — never wrapped (W5, see 1.6).
- **Slide 13's "UN"** ("DE PEDIR Y REZAR A UN PROCESO", SVG label) is the Spanish article — never wrapped (whole-token rule, S2, see 1.6).
- **Slide 15's first UX use** is inside an SVG `<text>` label ("arquitectura y UX"); visible-text UX begins on slide 16.
- **Case variant "SpecWeaver"** appears only inside the token "UN-SpecWeaver" (rail "6. UN-SpecWeaver", kicker "22 · UN-SpecWeaver", README module 6) — whole-token wrap with the SPEC-WEAVER tooltip (B-F7b, see 1.6).
- **Slide 22 hosts no standalone IA** — ledger S1's "IA (heading)" was not corroborated by re-verification (0 matches inside the data-index-22 article); the five verified sigla groups are all in reference prose (see Round-1 fix note, §4).

### 1.5 Technical approach

1. **Single source of truth**: the executor generates all wrappings from section 1.3, and the
   verification protocol re-checks against the same table.
2. **HTML text layer**: within the §1.6 scan surface (visible text nodes), wrap each occurrence as
   `<abbr title="Tooltip (final copy, §1.3)">SIGLA</abbr>`. At the first occurrence per slide unit of a
   *target-set* sigla, the visible text becomes the `Inline (final copy)` string from §1.3 inside the same
   `<abbr>`. Comments, attributes, `<head>` title and URLs are excluded surfaces (see 1.6).
3. **SVG layer: REVERTED (user override).** The 45 SVG `<title>` wraps were implemented, then removed —
   all 19 `<svg>` blocks are byte-identical to HEAD (verified). No SVG changes remain; diagram labels are
   pristine. (Original approach: nested `<tspan><title>…</title>SIGLA</tspan>`; obsolete now.)
4. **CSS affordance**: add to `assets/css/styles.css` one scoped rule, e.g.
   `abbr[title] { text-decoration: underline dotted; text-underline-offset: 2px; cursor: help; }`,
   consistent with the deck's existing tone/typography; no JS changes.
5. **Markdown docs**: inline HTML `<abbr title="…">` at the target occurrence in visible prose (GitHub renders
   inline HTML). README/demos: first use per document gets the inline expansion; subsequent uses hover only.
   **Fenced code blocks are excluded surfaces** (README GCPDSLAB clone URL; demos/02 IA + SDD inside ```prompt;
   demos/04 AWS/GCP/HTML/CSS/JS inside ```prompt) — no wrapping inside them. Where a document's first use is a
   partial expansion (README SDLC: "del desarrollo de software (SDLC)" en español) or falls inside an excluded
   fence, the executor is **authorized to make a definition-only insertion** at the nearest visible occurrence
   (§1.6, B-S1).
6. **Cover + global chrome**: hover only (no inline expansion) for IA, DIEEC, UNAL, and "UN-SpecWeaver"
   as one whole token (SPEC-WEAVER tooltip).

### 1.6 Exact exclusion rules, ambiguous cases, and scan surface

**Scan surface definition (JD-PLAN-002 / S2).** The hover+scan rule operates over exactly two surfaces:
**(a)** visible HTML text nodes (rendered content of `p/li/h2/h3/strong/span/a/td/th`, etc.) and
**(b)** visible SVG `<text>` content (including `<tspan>` runs). Everything outside those two surfaces is out
of scope by default. Documented exclusions, with reasons:

- **HTML comments** — not rendered; carry no visible siglas.
- **Attribute values** (`aria-label`, `alt`, `title`, `data-*`, `src` file names) — not visible text; e.g. the
  slide-14 (data-index 14) aria-label "…contrato previo al codigo (SDD o TDD)…" and the slide-21 diagram
  aria-label mention many siglas without rendering them. **Accepted deviation:** screen-reader users hear bare
  siglas inside aria-labels; they are deliberately left unwrapped (no visible surface to carry an `<abbr>`).
- **Markdown fenced code blocks** — code/spec/prompt content, not prose (README ```bash clone URL with GCPDSLAB;
  demos/02 ```prompt with IA + SDD; demos/04 ```prompt with AWS/GCP/HTML/CSS/JS).
- **The `<head>` document title** — not part of the slide/doc layer.
- **URLs** — non-text tokens; may embed sigla-like substrings (e.g. the GCPDSLAB handle in the clone URL).

**Whole-token rule (makes "assert every occurrence is wrapped" satisfiable).** Each sigla is wrapped only as a
whole defined token; partial matches are never wraps inside larger tokens: `\bUN\b` matches ONLY inside the token
"UN-SpecWeaver" — the Spanish article in the slide-13 SVG label "DE PEDIR Y REZAR A UN PROCESO" is never wrapped;
`\bPR\b` not inside "PRD" or "SWEPR"; `\bAI\b` not inside "OpenAI"/"Moonshot AI"/"Zhipu AI"/"GenAI";
`\bDevOps\b` not inside "Azure DevOps" (W5 — verified 3+ occurrences incl. SVG text on slide 21); `\bUX\b` not
inside "UX-DR"; `\bUN\b` not inside "UNAL".

- Product names that are not siglas get **no hover**: Azure, SQLite, Kimi, Qwen, DeepSeek, Claude,
  Codex, Astra, Fable, Slack, Discord, Jira, Miro, Notion, Confluence, HubSpot, Monday, Linear,
  Bitbucket, Sonar, Sentry, Jenkins, GitHub, GitLab, MS Teams (product name). This includes the
  "Azure DevOps" whole token (product name) and "Azure Boards".
- "AI" is wrapped only at standalone uses; "Moonshot AI", "OpenAI" and the compound "GenAI" (Veracode reference) stay unwrapped.
- "LLMs" (plural) is wrapped as a whole unit with the LLM definition; the singular "LLM" uses its own target-set row.
- "GPT-6 Astra": the "GPT" prefix is wrapped; "Astra" is not.
- "SWE-bench Verified": only the "SWE-bench" token is wrapped.
- Case-sensitive matching for mixed-case siglas (DevOps, SPEC-WEAVER, SWE-bench, FTS5, labIA); the case variant
  **"SpecWeaver"** gets the same SPEC-WEAVER tooltip and is wrapped only inside the whole token "UN-SpecWeaver" (B-F7b).
- **FR / UX-DR tokens are out of scope (A13):** "FR-1, FR-2…", "FR/UX-DR" and "FR-1…" (slides 17–18) are
  requirement identifiers, not inventory siglas — no hover, no definition insertion; `\bUX\b` must not match
  inside "UX-DR".
- **Definition-only insertions authorized (B-S1):** where a document/slide first use is currently a partial
  expansion (README SDLC: "del desarrollo de software (SDLC)" en español) or falls inside an excluded surface,
  the executor may insert the canonical English term + sigla at the nearest visible occurrence (definition-only;
  no rewording of surrounding text).
- Ambiguous per-occurrence decisions are frozen case-by-case in the executor notes; anything
  the executor cannot resolve cleanly becomes a flagged row for the user, not a guess.
- **Scan script status (B-S1):** the verification scan script is transient and lives under `odd/`;
  it is committed only with explicit user approval.

### 1.7 Verification protocol

After implementation (post-approval), run with `gentle-ai-verify`:
1. **No bare siglas**: an SVG-aware scan over the §1.6 surfaces (a) + (b), with the documented exclusions
   applied, asserts every occurrence of every inventory sigla is wrapped in `index.html`; the same scan over
   README/demos visible prose. HTML comments, attributes (aria-label/alt/title), Markdown fences, the `<head>`
   title and URLs are not scanned.
2. **First-use expansions**: per slide unit, each target sigla's first appearance in the **visible text layer**
   carries the exact `Inline (final copy)` string from §1.3. Slide units whose only occurrence is SVG-only
   (QA, TDD, BYOK; PR/MR/GH on slide 21) are **exempt** from the text-layer first-use assertion (W4).
3. **Definition consistency**: every tooltip for a given sigla equals the `Tooltip (final copy)` cell in §1.3 exactly.
4. **Pure-text no-rewording diff (W4)**: strip the `<abbr title="…">…</abbr>` and `<tspan><title>…</title>`
   wrappers from pre- and post-implementation files; the resulting pure-text diff must be **empty**.
5. **Exact-format assertion (W4)**: every inline expansion matches its §1.3 `Inline` string verbatim
   (`English canonical (SIGLA)` enforced).
6. **Parse integrity (W1)**: parse `index.html` with an SVG-aware parser (e.g. lxml foreign-content model —
   `html.parser` alone lacks it) with no tag-stack errors; `git diff --stat` shows only the intended files
   (index.html, assets/css/styles.css, README.md, demos/*.md, odd/*).
7. **Visual smoke (simplified after user override)**: layout smoke over every text-expansion slide
   (slides 1, 4, 12, 15–18, 20, 21) and the README rendering — optional/manual (the browser-based run was
   cancelled by the user as too slow; SVG tooltip smoke is obsolete since the SVG layer is reverted).
8. **Scan script**: transient, kept under `odd/`; committed only with explicit user approval (B-S1).

### 1.8 Scope discipline

- Only files: `index.html`, `assets/css/styles.css`, `README.md`, `demos/*.md`, `odd/*` tracking (+ the transient
  scan script under `odd/`, committed only with explicit user approval).
- No content rewording, no reflowing of diagrams, no JS behavior changes, no commits (user-owned).
- Definition-only insertions may add the canonical term + sigla at first uses (authorized, §1.6); nothing else changes meaning.

---

## 2. Tasks

- [ ] T1 — Explore + freeze decisions (done: this document)
- [ ] T2 — Judgment Day: dual blind review of the frozen plan (in progress)
- [ ] T3 — Merge findings into ledger; scoped fix round only for both-confirmed severe findings; re-judge (≤2 rounds)
- [ ] T4 — (after APPROVED + user go-ahead) Implement: canonical table → index.html text layer, SVG layer, styles.css, README, demos
- [ ] T5 — Verify per protocol 1.7; report failed/skipped checks; next step (commit/push remain user decisions)

## 3. Judgment Day — Round 1 findings ledger (frozen)

Judges: `jd-judge-a` (task muevtab2-1-q9be), `jd-judge-b` (task muevtabe-2-6evk); both returned "needs changes".
Severities: S=SEVERE, W=WARNING, G=SUGGESTION, I=INFO. `[A]`/`[B]` = reporter. Parent verified single-judge claims.

### Confirmed severe (both judges)
- **S1 [A1,B-F1] — Placement map omits the Fuentes slide and misattributes slide 21.** Deck has 23 `<article>` units: cover + slides 1–21 + `is-wide` "23 · Fuentes" (data-index 22) carrying AI ×6, DORA ×2, METR ×1, LLMs ×1, SWE-bench ×1, IA (heading). Slide 21's real siglas: SPEC-WEAVER, Azure, DevOps, MCP, SDD, ODD, API, PR, MR, GH, UN (kicker "22 · UN-SpecWeaver"). IA/AI/UNAL/DIEEC/SWE-bench/METR/DORA do NOT occur on slide 21.
- **S2 [A3,B-F7+F8] — Scan surface undefined.** Bare inventory siglas exist in HTML comments, attributes (aria-label/alt; e.g. slide-15 aria-label "…SDD o TDD…", slide-22 aria-label), fenced code (README GCPDSLAB clone URL; demos/02 prompt-fence SDD/IA; demos/04 AWS/GCP), the `<head>` title, and inside the SVG label "DE PEDIR Y REZAR A **UN** PROCESO" (Spanish article false positive, verified @~98853). "Assert every occurrence is wrapped" is unsatisfiable as written.
- **S3 [A4,B-G1+G3] — §1.3 mixes executor meta-labels with user-facing strings.** SPEC-WEAVER canonical "(deck's proposed stack name)", IA canonical "— (sigla en español)", DIEEC/GCPDSLAB gloss cells are the ⚠ notes themselves, UN unflagged though never expanded in the repo (same epistemic status as DIEEC). Tooltip/inline strings must be final user-facing copy.

### Confirmed warnings
- **W1 [A9,B-H1] — SVG `<tspan><title>` tooltips are browser-dependent** (Safari generally no native tooltip; Firefox historically patchy; `html.parser` lacks SVG foreign-content model). Need stated fallback/scope + 3-browser smoke (single-label `<text>` and multi-sigla `<tspan>` run).
- **W2 [A10,B-H3] — Layout risk from inline expansions** on dense slides (slide 1 "DevOps con CI-CD", slides 15–18, 20–22) across the 5 responsive breakpoints; smoke test must cover every expansion slide, not just slide 21.
- **W3 [A6,B-F4] — README/demos rows incomplete:** README IA ×6+, HTML/CSS/JS, PO, PRD, SPEC-WEAVER, GCPDSLAB (fenced); demos IA, LLM singular, AWS/GCP (fenced), SDD first-use inside a ```prompt fence in demos/02.
- **W4 [B-V1+V2,A4-tail] — Verification gaps:** no pure-text no-rewording diff (strip `<abbr>`/`<tspan><title>`, compare pre/post), no exact-format assertion `English canonical (SIGLA)`, "first appearance in the text layer" must exclude SVG-only units.
- **W5 [A7,B-F9n] — "Azure DevOps" collision:** `\bDevOps\b` matches inside excluded product name (verified 3+ occurrences incl. SVG text).

### Single-judge suspects (parent-verified)
- **A5 refuted:** Judge A's "TDD text-layer occurrence" is an aria-label attribute, not visible text — TDD remains SVG/attribute-only; no deviation change needed beyond S2.
- **B-F7b (fold into W-rules):** case variant "SpecWeaver" (rail button, kicker, README) needs an explicit disposition.
- **A8/B-F7c confirmed:** singular "LLM" (demos/04 L14) uncovered — add LLM/LLMs row.
- **A13:** FR / UX-DR tokens (slide 19) need an explicit out-of-scope note in §1.6.
- **B-S1:** README SDLC first-use is a Spanish partial expansion, not the locked format — authorize definition-only insertions (they are the user's ask); demo-04 title first-use (SDD) resolved as title hover-only, first body occurrence carries the inline expansion; scan-script file status: transient, under `odd/`, committed only with user approval.

## 4. Evidence log

- 2026-XX-XX: plan frozen; judgment day launched by parent orchestrator.
- Scoped re-judgment (round 1/2): both judges verified all three authorized findings resolved against the repo; verdict **approved** (see §5).
- **Implementation (T4)**: gentle-ai-worker applied the approved plan (71 `<abbr>` text wraps + 19 per-slide
  inline expansions + chrome wraps in index.html; one scoped CSS rule; README/demos inline-HTML wraps).
- **USER OVERRIDE (post-implementation)**: revert the diagrams to the original and keep hover only on text.
  The 45 SVG `<title>` wraps were removed; all 19 `<svg>` blocks are byte-identical to HEAD (verified).
  Browser-based visual smoke (T5 item 7) cancelled by user as too slow; programmatic checks passed
  (tag balance 23/23/71/1; 0 real bare siglas on the visible text surface — remaining 2 tokens are the
  documented exclusions "Azure DevOps" and "AI Copilot"; `<head>` title intact).
- **Quick screenshot pass (user-approved, Chromium headless)**: all 23 slides × 3 viewports
  (1440×900 desktop, 390×844 mobile, 844×500 compact) → `bodyOverflow = 0px` on every slide; no
  horizontal overflow anywhere, including the expansion slides (1, 4, 12, 15–18, 20, 21). Render check:
  71/71 `<abbr>` visible with `title`, computed style `text-decoration: underline dotted`, `cursor: help`;
  inline samples render correctly ("Development + Operations (DevOps)", "Continuous Integration /
  Continuous Delivery (CI-CD)", "Product Owner (PO)", …). Screenshots: `/tmp/sigla_shots/`.
- Round 1 both judges: "needs changes"; ledger persisted above; user authorized fix round.
- **Round-1 fix applied** (Judgment Day correction batch 1/2, fix agent): §1.3–§1.8 rewritten;
  §1.1, §1.2, §2 and §3 (frozen ledger) untouched. Rollback boundary: `git restore odd/tasks/siglas-definiciones-hover.md`
  (single-file fix — no other file touched, no git mutations run).
  - **JD-PLAN-001 (S1):** placement map now reflects the real 23 `<article>` units (cover + slides 1–21 +
    is-wide "23 · Fuentes", data-index 22); slide 21 restricted to its verified siglas (SPEC-WEAVER, DevOps,
    MCP, SDD, ODD, API, PR, MR, GH; Azure as excluded product name; UN only inside the kicker
    "22 · UN-SpecWeaver"); slide 22 (Fuentes) added with AI ×6, DORA ×2, METR ×1, LLMs ×1, SWE-bench ×1;
    cover/chrome corrected (cover: IA + UNAL img alt; "UN-SpecWeaver" in the rail button and slide-21 kicker;
    DIEEC + UNAL + IA in the footer running-title "DIEEC-UNAL-Manizales."); slide 11 IA and slide 15
    UX-first-in-SVG added; slide 7 "AI" marked exclusion-only; count sentence updated to 23 units.
  - **Evidence note (discrepancy vs. ledger S1):** S1 lists "IA (heading)" among slide 22's siglas; re-verification
    of `index.html` (data-index-22 article: full-text and raw token scans) found **zero** standalone IA inside that
    article (the heading is "Fuentes"; closest IA occurrences are in the footer running-title, attributed to global
    chrome). The map therefore records the five verified groups and flags "IA (heading)" as not corroborated;
    re-judgment decides whether the ledger claim or the repo is authoritative.
  - **JD-PLAN-002 (S2):** §1.6 now opens with a "Scan surface definition" — surfaces (a) visible HTML text nodes
    and (b) visible SVG `<text>` content; documented exclusions with reasons (HTML comments, attribute values
    incl. aria-labels with the screen-reader accepted deviation, Markdown fenced blocks, `<head>` title, URLs);
    whole-token rule makes "every occurrence is wrapped" satisfiable — "UN" is wrapped ONLY inside
    "UN-SpecWeaver" (slide-13 Spanish article excluded).
  - **JD-PLAN-003 (S3):** §1.3 restructured so every row carries exact user-facing Tooltip + Inline final copy
    plus a segregated executor-data column; meta-labels and ⚠ notes removed; DIEEC / GCPDSLAB / UN / SPEC-WEAVER
    strings set per controller copy ("Departamento de Ingeniería Electrónica y de Computadores (UNAL Manizales) —
    expansión no publicada en el repositorio (inferida)"; "Organización de GitHub del laboratorio — expansión no
    publicada en el repositorio"; "Universidad Nacional" flagged as not expanded in the repo; SPEC-WEAVER tooltip
    with inline staying "SPEC-WEAVER").
  - **Folded-in corroborated ledger items:** W1 SVG tooltip fallback + 3-browser smoke (§1.5/§1.7); W2 layout smoke
    over every expansion slide (1, 4, 7, 8–10, 12, 15–18, 20, 21, 22); W3 README/demos rows completed fence-aware;
    W4 pure-text diff, exact-format assertion, SVG-only exemption; W5 "Azure DevOps" whole-token exclusion;
    LLM (singular) target-set row + LLMs plural note; "SpecWeaver" case-variant disposition (same tooltip,
    whole-token "UN-SpecWeaver"); FR / UX-DR out-of-scope note; definition-only insertions authorized;
    scan script transient under `odd/`.
  - **Remaining risks:** (1) the S1 "IA (heading)" discrepancy above — unresolved, flagged for re-judgment;
    (2) "APIs" (plural, slide 3 text) is not inventoried in this plan but exists in deck prose — outside the three
    authorized findings, not touched; (3) tooltips with nested parentheses (DORA, MR, NIST, GLM, BYOK, LIA) keep the
    judge-verified glosses verbatim and may read slightly awkward, but remain content-faithful.

## 5. Final verdict + residual handoff notes (post re-judgment)

**JUDGMENT: APPROVED** (round 1/2 re-judgment; both blind judges: `rejudgment: approved`).

- Target identity (fix delta sha256): `9d93e114088759d460d3dde553e6a3a45bc256bfe41caf7a0f6693cfed7754ed`.
- Fix work units: 3 (JD-PLAN-001, JD-PLAN-002, JD-PLAN-003) + folded ledger items, one file
  (`odd/tasks/siglas-definiciones-hover.md`), rollback `git restore` of that file.
- Resolutions verified by both judges against the repo: JD-PLAN-001/002/003 — all `verified`.
- S1 "IA (heading)" discrepancy: **resolved in the repository's favor** (zero standalone IA inside the
  data-index-22 article; the ledger claim was a misattribution of the footer running-title).
- Confirmed severe: 3. Suspects resolved: 5 (of which A5 refuted). Contradictions: 0.
  New non-blocking findings after the fix: 0 CRITICAL, 0 HIGH.
- Skill resolution: none (no matching project skill; plan-document target).

**Residual handoff notes for the executor (advisory, not re-judged):**
1. **API on data-index 7 is SVG-only** (corroborated by both judges + parent re-check: 0 text-layer
   occurrences; SVG 'tarifas oficiales de API', 'suscripción o API' ×2 + 1 aria-label). Executor data in
   §1.3 says "text + SVG" — execute as SVG-only (first-use exemption W4); slide 21 stays text + SVG.
2. **Pure-text diff (1.7 check 4)** must read "empty **except** authorized first-use inline insertions
   (§1.5 p.2) and definition-only insertions (§1.6 B-S1)" — judge B MEDIUM; executor qualifies the check.
3. **DIEEC/GCPDSLAB tooltips** end with "— expansión no publicada en el repositorio (inferida)" — this is
   intentional honesty copy (controller-authored, user-confirmed epistemic flags), accepted as-is; if the
   user prefers purely definitional tooltips, move the clause to the Executor column only.
4. UN executor note wording: expansion "Universidad Nacional de Colombia" IS present in cover/README;
   the tooltip "Universidad Nacional" and wrapping rules are unaffected.
5. FR / UX-DR tokens are all on data-index 17 (not 18); out-of-scope note stands.
6. Azure DevOps counts: 3 raw occurrences (2 visible text/SVG + 1 aria-label) — one counting basis to use.
7. Slide numbering convention: "slide N" in this doc = data-index N = visible kicker N+1.
8. "AI Copilot" (GitClear report title, slide 22) and hyphenated compounds "AI-assisted"/"AI-generated":
   treat as product-name/compound exclusions (no hover), consistent with "GenAI.

---

## 6. Evidence log (continued)