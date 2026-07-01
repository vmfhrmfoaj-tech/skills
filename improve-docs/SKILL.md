---
name: improve-docs
description: Explore a project's documentation and link structure to identify fragmentation, duplication, and unclear document roles, then improve them by creating a cohesive documentation architecture with clear single sources of truth (SSOTs). Use for documentation architecture cleanup, consolidation of shallow docs, SSOT designation, ADR/reference classification, duplicate removal, and broken-link repair. Do not use for isolated typo fixes or a single wording change.
---

# Improve Docs

Reduce the cost of navigating and maintaining documentation. Keep related information together so readers can understand it in context. Maintain each fact in one authoritative location, and enable readers to find what they need by opening as few documents as possible.

If the user provides a target path or goal, treat it as the scope of the investigation. Otherwise, investigate documentation across the repository, but do not modify anything until you have presented candidate improvements and the user has selected their scope.

## Evaluation Criteria

Use the following questions to identify friction in the documentation structure. Do not base conclusions on a checklist score alone. Base them on the actual navigation overhead and confusion encountered while exploring the repository.

- Must a reader repeatedly move between several short documents to understand one concept?
- Does a document merely redirect the reader instead of providing useful information itself?
- Is the same fact maintained independently in multiple documents?
- Are the roles of ADRs, which preserve decision-time context, and continuously updated references mixed together?
- Would removing a document and merging its content into the canonical source simplify navigation and maintenance?
- Can readers predict where information lives and what role a document serves from entry-point documents, titles, and links alone?

Treat documents with the same topic, audience, and change cadence as consolidation candidates. Do not force documents together when their change cadences differ or they need to be read independently.

## Process

### 1. Explore

First, read the repository instructions and root entry-point documents. Then inspect the documentation tree within scope, each document's role, relative links, anchors, orphaned documents, and broken links.

Read the code and configuration described by the documentation to verify facts. Use code and configuration only as evidence; do not modify them with this skill. Read existing ADRs, and do not reopen settled decisions without evidence.

### 2. Identify Improvement Candidates

Cluster related documents according to friction actually encountered during exploration. Include the following information for every candidate:

- **Scope**: The relevant documents and the topic they cover
- **Problem**: Observed friction, such as navigation overhead, duplication, unclear roles, or broken links
- **Proposed change**: What to keep, consolidate, move, or delete, and which document should become the canonical source
- **Benefit**: How the change reduces navigation and duplicate-maintenance costs
- **Risk**: Potential information loss, broken external links, conflicting change cadences, or other concerns
- **Recommendation strength**: One of `Strongly recommended`, `Worth considering`, or `Speculative`

If there are no worthwhile candidates, do not invent any. Report what you investigated and why no improvement is necessary.

### 3. Present Candidates and Obtain Approval

Present candidates in recommendation order in the chat. State which candidate should be addressed first and why. Do not create a separate planning document or HTML report.

Do not make structural documentation changes—such as consolidation, relocation, or deletion—until the user selects a candidate and explicitly approves the scope. Do not modify documents while waiting for approval. If a simple link repair or wording reduction falls outside the approved scope, disclose it and obtain approval before proceeding.

### 4. Modify

Process one selected documentation cluster at a time. Keep diffs small and follow these principles:

- Keep each duplicated fact in the single document that is most authoritative and updated first. Replace other copies with relative links.
- When consolidating fragments, preserve proper nouns, commands, code, error messages, evidence, and meaning.
- Keep decisions whose date and rationale are fixed in ADRs. Keep continuously changing information—such as glossaries, current status, and operational procedures—in living references.
- Update every internal reference to a document that was moved or deleted.
- Follow the repository's conventions for prose style, location, filenames, frontmatter, and links. Do not impose a new schema unless the repository requires it.

### 5. Validate and Report

After making changes, verify all of the following:

- No references remain to paths that were moved or deleted.
- Relative links and internal anchors resolve to real targets.
- Entry-point documents and indexes accurately reflect the current documentation structure.
- No facts, constraints, or decision rationale from before the consolidation were omitted or had their meaning changed.
- No document within the approved cluster still duplicates a fact maintained elsewhere in that cluster.

Report the documents changed, the designated SSOTs, the validation performed, and any unresolved risks.

## Safety Boundaries

- Modify documentation files only. Do not change code, runtime configuration, types, or generated artifacts.
- If repository instructions conflict with the user's request, stop and explain the conflict.
- Do not invent uncertain facts or designate an unsupported canonical source. Obtain evidence from code, configuration, ADRs, or the user.
- Do not discard information during consolidation. If the value of deleting something is unclear, preserve it and report the risk.
- Do not make changes beyond the candidates and scope approved by the user.
