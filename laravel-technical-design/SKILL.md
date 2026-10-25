---
name: laravel-technical-design
description: Turn a supplied product requirements document into a Laravel technical design through a user-led interview, one question at a time. Use only when explicitly invoked for Laravel technical design, not for automatic design generation or implementation.
---

# Laravel Technical Design

Help the user decide what will be built and how it will work. Produce a technical design in simplified technical English that one or more engineers can use to implement the supplied PRD consistently and later divide into work packages.

This is an explicitly invoked design interview. It does not authorise application implementation, dependency installation, infrastructure provisioning, or deployment.

## Establish the source

Read the supplied PRD and any explicitly identified supporting requirements. If no PRD is available, ask for its content or location as the single next question. Do not start a generic architecture questionnaire in its place. If a native text question cannot accept an attachment, ask in ordinary chat for the document.

Preserve requirement IDs and domain language. For unnumbered requirements, assign reference IDs without changing their meaning. Identify contradictions, missing product behaviour, and decisions already established by the PRD or conversation. A PRD supplied for this task is a requirements source; an unrelated file, existing implementation, or research finding is context until the user adopts it as a constraint.

Clarify whether this is a new application or a change to an existing one if not established. Inspect relevant existing project material when available and authorised, but ask which existing architectural choices must be preserved rather than adopting them silently.

Read [references/design-coverage.md](references/design-coverage.md) after reading the PRD to identify applicable decisions. Revisit relevant sections when preparing the output. It is a coverage guide, not a fixed interview or a list of features to add.

## Domain terminology and bounded contexts

Treat the PRD's user-agreed domain glossary as the source of domain terminology. If the glossary is missing, incomplete, or ambiguous for the affected work, establish the missing terms with the user one question at a time before designing components that depend on them. Do not invent meanings, substitute familiar synonyms, or silently rename concepts.

Apply domain-driven design through a ubiquitous language within each explicitly agreed bounded context: the same term must have the same agreed meaning throughout that context's requirements, design, model names, relationships, operations, events, interfaces, API contracts, UI labels, and verification scenarios. Language-level naming forms such as singular class names, plural table names, and casing may vary without changing domain meaning; follow agreed naming conventions. Do not force unrelated technical infrastructure concepts into the domain glossary.

Establish each context's purpose, terminology, model responsibilities, and boundaries with the user. Do not infer a context from a UI area, role, database table, or module. Do not assume separate services or databases, or introduce aggregates, repositories, or other DDD patterns solely to claim DDD compliance. Propose these only when they solve a relevant design need and obtain agreement.

The same word may have different meanings in different contexts. Record each meaning with its context instead of forcing a global definition or shared model. Where contexts interact, agree ownership of concepts, the information exchanged, and explicit mappings or translations at the boundary. Resolve conflicts between the PRD, existing code, and proposed names with the user; do not silently rewrite the glossary or existing code.

In the document, reference the authoritative glossary and include agreed context-specific additions or mappings in one place. Keep terminology consistent without duplicating definitions across sections. Proposed glossary changes remain questions until accepted.

## Ask one question at a time

Use the available native structured question UI. Prefer `request_user_input_async` when exposed; use `request_user_input` only when its active-mode and usage restrictions permit. Follow the actual tool schema. Do not change modes to gain access to a question tool.

- Submit exactly one focused question per call and wait for its answer. Do not combine separate choices in one question or send another pending question.
- For a design choice, offer two or three concise, meaningful alternatives. Explain their practical trade-offs in option descriptions where supported, or in a brief sentence before the question.
- Mark an option `(Recommended)` only when the recommendation is grounded in the requirements and known constraints. Explain the reason. If no choice is justified yet, ask the prerequisite question instead.
- Preserve a free-text answer through the tool's built-in convention. Do not add an artificial Other option where the UI already provides it. Use a native free-text question for information that does not have useful bounded choices.
- If native questioning is unavailable or disallowed, explain that briefly and ask one question in ordinary chat with concise choices where useful. Do not imitate interactive controls.
- With an asynchronous question, end the turn after the question or continue only independent read-only research. Wait for an actual user reply before dependent work or the next question. Silence, a preselected option, a timeout, or an empty response is not a decision.

Choose the next question from the most consequential remaining uncertainty. Establish choices that constrain others before their details: for example, application surfaces before UI components, and hosting constraints before production process configuration. Reuse clear prior answers. Do not ask for every checklist item regardless of relevance.

Make technical choices approachable. Briefly explain unfamiliar terms and consequences so the user can decide. For detailed contracts, present a focused proposal for one coherent component and ask whether to adopt or change it. Do not use a single approve-everything question to hide unrelated decisions. If the user is unsure, explain or research the alternatives and return to the choice; do not choose silently.

## No unconfirmed design decisions

Every substantive requirement, design decision, component contract, and operational setting in the final design must trace to details explicitly supplied or agreed by the user, including requirements documents they explicitly adopt as authoritative. If a supplied document's authority or a detail's intended meaning is unclear, ask rather than treating it as agreed. Rephrasing, organising, and assigning reference IDs are allowed. Adding meaning is not. Examples, verification scenarios, rationale, exclusions, and numeric settings must not introduce unagreed details either.

Recommendations remain proposals until accepted. This includes conventional choices such as the Laravel version, frontend stack, database engine, directory structure, class names, packages, roles, routes, queue drivers, retry counts, time zones, hosting provider, and performance targets. Do not fill gaps with best practice, familiar defaults, or what seems obvious.

A user can explicitly adopt a clearly described proposal or bounded set of conventions; reuse that decision without reconfirming each consequence already stated. If asked to choose on the user's behalf, explain the proposed decision and obtain their acceptance before recording it as agreed. A request to finish is not acceptance of unstated choices.

Keep a concise working decision ledger in the conversation context:

- **Confirmed:** decision ID, exact choice, source requirement or user answer, rationale when supplied, and affected components.
- **Proposed:** recommendation, evidence, and alternatives still awaiting a choice.
- **Open:** unanswered question, why it matters, and what it blocks.

Use short checkpoints after a coherent topic, without repeatedly dumping the ledger. Clarify contradictions one question at a time. When an answer changes, update the ledger and revisit affected contracts. Keep proposals out of committed design sections. Do not create an assumptions section.

## Ground recommendations in current Laravel capabilities

Use official, version-matched Laravel documentation for relevant recommendations. If the version is undecided, verify supported options and ask the user to choose; never hard-code a remembered latest version. Verify relevant package compatibility from official package documentation. Record selected versions and link sources near consequential feature choices.

Research only capabilities relevant to the product and unresolved decisions. Use the coverage guide to consider framework features and first-party packages without turning the design into a catalogue. If documentation access fails, state the limit and keep affected technical claims unverified rather than presenting them as established facts.

Distinguish framework facilities from application conventions and third-party packages. For example, Policies are Laravel facilities; an `ApproveApplication` action is an application-defined component; an outbox requires an explicit implementation decision. Do not imply Laravel provides a complete role-management, tenancy, audit, workflow, or exactly-once delivery system automatically.

## Build a coherent specification

Develop the design around product workflows and shared contracts. Name the Laravel features and agreed components that implement each requirement. Define responsibility, inputs, outputs, authorisation, state changes, transactions, failures, and side effects with enough precision that engineers need not invent behaviour.

Cover routes and navigation as well as backend design. Keep page routes, menu structure, and API endpoints distinct but linked. UI and API entry points must have agreed relationships to shared business operations; do not assume the UI consumes the public API.

Treat local development and production deployment as design decisions. Specify the selected runtime approach, services, environment differences, everyday workflows, delivery pipeline, release sequencing, and recovery behaviour. Do not assume containers, a cloud provider, SQLite for tests, synchronous local queues, or any other setup.

Use the coverage guide to check omissions throughout the interview. Unexplored means **Not yet established**, not **Not applicable**. A reasoned exclusion or decision that no extra component is needed is a useful confirmed outcome. Do not add dashboards, billing, AI, multi-tenancy, or other product scope simply because Laravel supports them.

## Write and hand off

Continue one-question-at-a-time discovery until applicable decisions and contracts are consistent and resolved. Do not stop after a fixed number of questions. Avoid endless interviews by accepting complete answers and resolving related detail through focused proposals.

When the design is ready, briefly summarise its major agreed decisions and proceed to writing under the original request; do not add a ceremonial approval step. If unresolved choices remain and the user wants an early output, identify those choices and ask, as the single next question, whether to continue discovery or produce a document with those exact gaps. Never invent answers to make the document look complete. Explain material limitations in the handoff conversation without adding a document status field or badge.

Ask for a save location as a separate question if none was supplied. Save Markdown unless the user requests another format. Do not overwrite unrelated files. For a large design, propose a linked structure and get agreement before splitting it; otherwise use one document. Do not create backlog tickets or implementation files as part of this skill.

Do not include project timelines, delivery dates, milestones, sprint plans, duration estimates, or effort estimates in the technical design, even when source material contains them. Describe implementation dependencies and deployment step order without assigning dates or durations. This does not exclude explicitly agreed application timing rules such as job schedules, retry delays, timeouts, or retention periods; never invent their values.

Use the document structure and technical-statement format in [references/design-coverage.md](references/design-coverage.md). Scale depth to the product. Give shared schemas and contracts one authoritative location. Keep coverage classifications in working notes; include agreed exclusions and substantive open questions where they affect implementation, without status labels or a coverage-status table.

Keep the document focused on the agreed design. Do not include administrative boilerplate such as document status, readiness labels, author/owner fields, approval or sign-off tables, document version numbers, revision histories, or empty template sections. This does not exclude technical versions, resource ownership rules, HTTP status codes, or application states needed by the design. Immediately below the title, a single `Last edited: YYYY-MM-DD` line may record the user's local date when the document is actually created or revised; do not add a time of day or invent a historical edit date.

Write in simplified technical English: short sentences, active voice, one rule per statement, consistent domain terms, and concrete verbs. Explain necessary jargon once. Use **must** for agreed obligations; keep recommendations and alternatives outside agreed obligations. Include precise component names and tables where useful. Avoid large code blocks, generated implementation code, interview transcripts, and vague terms such as "secure", "fast", or "handle errors" without agreed meaning. Type names, method names, route paths, and compact contract notation are useful without full code bodies. Do not claim formal ASD-STE100 compliance unless specifically required and verified.

Before delivery, verify:

- Each in-scope requirement maps to design statements and observable verification scenarios; omissions and exclusions are explicit.
- Every substantive design choice has an established source; proposed choices have not become requirements accidentally.
- The document contains no project timelines or estimates, and examples, scenarios, rationale, and operational values add no unagreed details.
- Administrative boilerplate and empty template sections are absent; any last-edited date reflects the actual edit in the user's local date.
- Schemas, permission rules, routes, UI behaviour, interfaces, event payloads, and environment settings agree across sections.
- Domain names and meanings match the agreed PRD glossary within each bounded context; context boundaries and cross-context translations are explicit user decisions, not inferred architecture.
- Contracts define relevant invalid inputs, denied access, duplicates, concurrency, rollback, and external failures without inventing outcomes.
- Dependencies and shared contracts allow later work splitting without forcing separate engineers to guess integration behaviour.
- Substantive open questions are visible. Do not claim the design can be implemented without further decisions while unresolved choices require engineers to make material product or architectural decisions.

Verify saved files and local cross-links. Return the document link and explain any remaining implementation blockers concisely, without a formal status label.
