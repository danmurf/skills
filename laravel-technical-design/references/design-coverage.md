# Design coverage and output structure

Use this guide to identify decisions after reading the supplied PRD, UX design package, or both and to check the final design. Questions are adaptive and asked one at a time; the sections below are not a questionnaire. Include a capability only when it serves confirmed requirements. Never populate a section with invented defaults.

## Document structure

Use these sections as a coverage outline, including only sections with substantive design content. Adjust depth and combine small related sections where useful. Omit empty template sections. For UI-only or API-only products, record the agreed excluded surface in scope rather than inventing it. Keep coverage tracking in working notes, not in the document.

Do not add administrative metadata such as status, readiness labels, authors, document owners, approvals, sign-off tables, document version numbers, or revision histories. A single `Last edited: YYYY-MM-DD` line immediately below the title is allowed, using the user's local date when the document is actually created or revised. Technical versions, application states, resource ownership rules, and HTTP status codes remain part of the design where required.

1. **Purpose, scope, and sources:** available PRD and UX design links and relevant source revisions, requirement and flow/screen IDs, authoritative domain glossary, included and excluded work. Identify the supplied starting point without requiring absent artifacts.
2. **Agreed architecture and versions:** application surfaces, boundaries, dependencies, stack, conventions, and consequential rationale.
3. **Domain language, contexts, rules, and workflows:** authoritative PRD glossary, agreed bounded contexts, context-specific meanings, boundary mappings, actors, invariants, states, transitions, and end-to-end operations.
4. **Data design:** schema, Eloquent mapping, query behaviour, and consistency rules.
5. **Identity and access:** authentication, authorisation matrix, and tenancy where required.
6. **UI areas, routes, and navigation:** route catalogue, menu tree, page contracts, and journeys, linked to accepted UX flows/screens where supplied.
7. **API contracts:** endpoints, schemas, access, errors, and compatibility.
8. **Application components and boundaries:** shared operations, interfaces, dependencies, and bindings.
9. **Events and background work:** events, listeners, jobs, schedules, and delivery semantics.
10. **Integrations and supporting capabilities:** applicable communications, storage, search, caching, realtime, billing, or AI decisions.
11. **Local development and environment matrix:** setup, services, test data, and daily workflows.
12. **Production architecture and delivery:** services, pipeline, release sequencing, operations, and recovery.
13. **Verification and quality targets:** requirement-linked scenarios, contract checks, and measurable operational targets.
14. **Implementation boundaries and dependencies:** coherent future work areas, shared contracts, prerequisites, and integration checkpoints.
15. **Traceability and open questions:** requirement-to-design links and any unresolved choices with their effects. Keep decision rationale beside the relevant design instead of adding an administrative decision log.

Keep detailed contracts in their own section and reference them elsewhere. Do not copy the interview transcript. Suggested work areas describe how the design can later be split; they are not estimates, assigned tickets, or permission to build. Exclude project timelines, delivery dates, milestones, sprint plans, duration estimates, and effort estimates throughout the document. Dependency order and deployment step order may be specified without dates or durations. Application timing rules require explicit user agreement and are separate from project planning.

## Technical design statement

Use a stable ID such as `TD-APP-012`. A statement or small related group should identify:

| Field | Required meaning |
|---|---|
| Requirement | Source requirement IDs, relevant UX flow/screen IDs where supplied, and the user decision establishing this design |
| Decision | A precise obligation describing what will be built or how it behaves |
| Components | Named Laravel facilities, application components, and selected packages |
| Contract | Inputs and types, outputs, actor/tenant context, permissions, and failures |
| Data and timing | Reads/writes, invariants, transaction boundary, and synchronous/asynchronous effects |
| Verification | Observable successful, rejected, and recovery outcomes linked to requirements |
| Dependencies | Other statement IDs or shared contracts needed for implementation |

Include rationale where it explains a real trade-off. Omit irrelevant fields rather than adding boilerplate. Open proposals belong in the unresolved-decision section, not in mandatory statements.

## Coverage prompts

### Architecture and domain

- New application versus existing feature; constraints to retain or deliberately change.
- Framework, PHP, database, frontend and package versions, with compatibility evidence.
- UI/API/console entry points and whether deployment units are shared or separate.
- Module responsibilities, permitted dependencies, namespace/directory conventions, and ownership of shared contracts.
- Domain vocabulary, entity ownership, invariants, state transitions and rejected transitions.
- Authoritative glossary terms and definitions, their agreed bounded contexts, and consistent use in Eloquent models, relationships, operations, events, contracts, UI and verification. Ask about missing or conflicting terms; do not silently invent or rename them.
- Context purpose and model responsibilities; boundaries and dependencies; ownership and translation of concepts exchanged between contexts. Different meanings in different contexts remain explicit. Do not equate contexts with screens, roles, tables, microservices, or separate databases.
- Rules for money, precision, rounding, dates, time zones and localisation where relevant.
- Distinguish request validation, permissions and business invariants. Specify where each is enforced across entry points.

### Schema and persistence

- Tables, columns, types, identifiers, nullability, defaults, indexes, uniqueness, foreign keys and deletion behaviour.
- Cardinalities, pivot attributes and Eloquent model/relationship names; casts, enums, writable attributes, scopes and serialisation restrictions.
- Query access patterns, tenant filtering, sorting, pagination, eager loading and expected volumes.
- Transaction owner, atomic writes, locking or conflict detection, duplicate requests and races. Specify database constraints as well as request validation where needed.
- Soft deletion versus permanent removal, retention, audit history and restoration.
- Reference seeds, factories, existing-data migration, backfills and compatibility during release.

### Identity and authorisation

- User lifecycle, login/logout, recovery, verification, MFA or SSO only where required.
- Sessions versus tokens, relevant guards, Sanctum or Passport where justified, token abilities, expiry and revocation.
- Permission matrix: actor/role, action, resource, ownership, tenant, state conditions, field restrictions and denial outcome.
- Named Policies and Gates, enforcement locations, role/permission storage and any selected package.
- Tenant resolution and isolation across queries, jobs, files, caches, integrations and channels where applicable.
- Request forgery protection, CORS and rate limits appropriate to agreed clients; sensitive-data handling, secret storage, encryption and audit access.

### UI, routes and navigation

- Accepted UX navigation, flows, screens, actions and states where supplied; map them to supporting contracts and reference the design package rather than duplicating mockups. Without UX, establish needed interface behaviour from the PRD and interview.
- Preserve accepted UX decisions and explicit PRD departures; resolve other source conflicts with the user. Keep unreviewed proposals, sample data, simulated behaviour and prototype-only technology distinct from production obligations.
- Public, authenticated, customer, organisation, settings and internal areas only when required.
- Route catalogue: HTTP method, path, route name, controller/component, middleware, binding/scoping, permission and requirement ID.
- Menu tree: hierarchy, labels, order, destinations, visibility, active states, and icons if agreed. Routes without menu entries and grouping nodes without pages are valid.
- Layouts, pages/components, displayed data, forms, field validation, actions and role-dependent states.
- Loading, empty, validation, failure, forbidden and not-found states; accessibility and responsive behaviour required by the product.
- Breadcrumbs, direct links, pagination/filter URL state, redirects, post-save/delete destinations and back navigation where relevant.
- Blade, Livewire, Inertia or separate frontend choice; division of frontend/backend responsibilities and shared operation contracts. Do not assume all validation uses Form Requests or that a browser action calls the public API.

### API

- Consumer and authentication model; path/method/name, request fields/types, required versus omitted versus null values, validation and authorisation.
- Response fields/types, permitted resource relationships, API Resources or another agreed format, status codes and stable error contracts.
- Pagination, filter/sort allowlists, rate limits, versioning and compatibility policy.
- Idempotency, concurrency, long-running operations and progress/status retrieval where required.
- Outbound/inbound webhooks, signature checks, duplicate and out-of-order delivery, timeouts, retries and reconciliation.
- OpenAPI or another agreed contract format when useful; do not generate executable handlers as the design.

### Operations and interfaces

- Named application operations, inputs/outputs, caller responsibilities, rules, state changes and domain failures.
- Shared behaviour across web/API/console; transaction and permission-check ownership across entry points.
- Interface operations, typed inputs/results, failure semantics, adapters, container bindings and test substitutes where boundaries justify them.
- Use concrete components when an interface adds no agreed value; do not invent repositories or layers automatically.
- Cross-module access and which components may write each entity or call external providers.

### Events, listeners, observers, jobs and scheduling

- Event names/meaning, producers, payload schema and identifiers, consumers, dispatch timing and schema compatibility where relevant.
- Explicit domain events versus Eloquent model lifecycle events; observer responsibility and paths such as bulk updates that may bypass model events.
- Listener responsibilities, synchronous versus queued execution and dependency/order requirements. Do not rely on unstated listener ordering for critical workflow steps.
- Queue connection/name, payload, timeout, attempts, backoff, idempotency, overlap protection, failure recording and replay procedure.
- Commit/rollback behaviour and whether processing can start before commit. After-commit dispatch is not atomic database-to-broker delivery; evaluate a durable outbox only when requirements justify it.
- Duplicate delivery, partial completion, safe retry, and recovery. Locks and unique jobs do not by themselves guarantee exactly-once external side effects.
- Schedule, time zone, daylight-saving behaviour, missed runs, overlap prevention, single-server execution and monitoring.

### Supporting capabilities

Consider only applicable features and verify version-specific support:

| Need | Candidate facilities | Decisions to establish |
|---|---|---|
| Communications | Mail, Notifications | Triggers, recipients, channels, templates, preferences, timing and duplicate handling |
| Files and images | Storage disks, temporary URLs, relevant processing tools | Ownership, private/public access, upload validation, processing, cleanup and retention |
| Integrations | HTTP Client, adapters, webhooks | Credentials, timeouts, safe retries, mapping, failures and reconciliation |
| Realtime | Broadcasting, Reverb, Echo | Channels, channel authorisation, payload privacy, reconnect and missed updates |
| Performance | Cache, Redis, atomic locks, concurrency tools | Keys, tenancy, TTLs, invalidation, stale reads and measurable benefit |
| Search | Database queries/search, Scout or selected engine | Fields, filters, ranking, access checks, indexing and freshness |
| Billing | Cashier or provider integration | Billing lifecycle, entitlements, webhook authority and reconciliation |
| Rollout | Pennant or agreed flag mechanism | Targeting, defaults, ownership, testing and removal |
| Operations | Artisan, health checks, logging/context, Horizon, Pulse, Telescope where suitable | Commands, signals, access, production suitability, redaction and retention |
| AI | AI SDK or selected provider integration | Data boundaries, provider/model, evaluation, failures, latency and cost limits |

### Local development and environment matrix

- Supported operating systems and local runtime approach: native tools, Herd/Valet, Sail/other containers, remote development or another user-selected option. Record versions and prerequisites.
- Database, Redis/cache, queues, mail capture, storage, search and realtime services; local versus shared location and lifecycle.
- Bootstrap steps, configuration variable names and sources, migrations, safe reference/test data and reset process. Never include real secrets.
- Commands or documented procedures to start/stop services, build/watch assets, run workers and scheduler, execute tests, inspect mail/logs and debug.
- External provider sandboxes, controlled fakes, webhook tunnels and offline/unavailable-provider behaviour.
- Environment matrix for local, automated tests, staging and production where those environments are agreed. Record service versions, configuration differences and how differences are tested.
- Do not imply SQLite tests exercise production database semantics, synchronous jobs exercise worker behaviour, or local files exercise object-storage behaviour. Agree the needed integration checks.

### Production, delivery and recovery

- Selected hosting provider and deployment approach; web processes, workers, scheduler, broadcast server, static assets and supporting managed services.
- Database/storage/queue/cache topology, persistence, network access, domains/TLS, secret configuration and access ownership.
- Agreed capacity/latency/availability targets and scaling approach; long-lived-process constraints if Octane or similar is chosen.
- Pipeline triggers, dependency installation, quality gates, tests, asset compilation, release artifact, staging/promotion and any agreed approvals.
- Configuration/route/view/event caches where applicable; migration and backfill order; mixed-version compatibility for requests, jobs and events.
- Worker/service reloads, graceful draining, health checks, smoke checks, rollback triggers/procedure and limits of database rollback.
- Backups, restore verification, agreed recovery targets, monitoring, redaction, alerts, failure recovery and support procedures.
- These are specifications, not authority to create cloud resources or deploy.

### Verification and later work splitting

- Map source acceptance criteria and supplied accepted UX flows, screens, actions and states to technical statements and observable checks. Cover denial, tenant isolation, invariants, invalid transitions, duplicate/concurrent requests, rollback, integration failure and recovery where relevant.
- Identify appropriate unit, feature, database, interface/contract, browser and production-engine checks; select Pest/PHPUnit and tools only by agreement.
- Name needed fixtures/factory states, real-service integration environments and measurable acceptance thresholds. Do not invent targets.
- Identify coherent implementation areas, prerequisite decisions, shared schemas/contracts and integration checkpoints so work can later be split among engineers.
- Do not include timelines or estimates. Keep staffing, ticket creation and application implementation outside the deliverable unless separately requested.

## Internal coverage review

In working notes, check each applicable area is specified, explicitly excluded with the agreed reason, or unresolved with a question ID. Do not equate unexamined with irrelevant. Do not export these classifications as document metadata, status badges, or a coverage-status table.

Include substantive open questions in the document only when unresolved choices remain. Identify affected requirements/components and what cannot yet be implemented consistently. Recommendations may accompany open questions but cannot masquerade as decisions. Explain implementation blockers in the handoff conversation without adding a document status field.
