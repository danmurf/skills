# Lightweight design deliverables

Produce enough for the user to recognise the application they want built: its areas, screens, navigation, main actions, and core journeys. Keep one short application-design document as the entry point. Do not create separate files or detailed specifications merely to fill a checklist.

## Application map and flows

Show the main areas and which screens belong in each, with navigation between them. Do not assume a dashboard is the landing page. Include relevant roles only where established by the PRD.

Use editable Mermaid flowcharts for core journeys: the user's goal, starting point, screen transitions, meaningful choices, and outcome. Keep diagrams at the level of tasks, screens, and meaningful decisions. Include a distinct progress or recovery screen only when central to the product experience.

Use simple flow and screen IDs when helpful and retain source PRD IDs. Render diagrams when supported; disclose unchecked rendering. A prose list alone is not a flow diagram.

## Screen mockups

Produce actual visual layouts using the selected shadcn variant and real components. Show what each main screen contains, its main actions, and how it relates to other areas. Use realistic illustrative content rather than lorem ipsum that hides layout problems. Do not invent business rules through sample content.

Start with rough wireframes where they help a decision and evolve the same layouts into clear, reviewed screen mockups. Target the agreed device or viewport; add other layouts only when useful or requested.

Use standard shadcn styling or an existing project theme, with consistent components and basic accessible design. Focus review on layout, content hierarchy, navigation, and main actions. Branding, colour palettes, typography exploration, and visual polish are optional extensions when requested or consequential to the experience. Include additional states when they help explain a core journey.

## Connected walkthrough

Link screens so the user can navigate the application and try its main journeys. Simulate only enough interaction to make the experience understandable; sample data and local state are sufficient. Identify simulated or unsupported actions. Do not invoke production services to demonstrate a flow.

Keep editable source and provide a preview link or concise launch instructions. Do not set up Storybook by default. If rendering cannot run, explain the limitation; unrendered source is not a reviewed visual mockup.

## Short design notes and review

The entry document should link to the mockups and walkthrough and briefly capture:

- Source PRD, scope, application areas, and each screen's purpose.
- Main journeys and important behaviour that is not obvious from the visuals.
- Accepted decisions, proposals awaiting review, agreed PRD departures, and unresolved questions.
- Relevant requirement links and areas deliberately left for later design.

Review the application with the user area by area. Invite them to walk a main task, explain what feels right or missing, and revise the mockups accordingly. Record actual acceptance without turning review into an administrative sign-off process. Do not require formal research participants, test scripts, or a usability report unless requested.

Hand off the agreed screen structure and experience, relevant source requirements, and material unresolved choices to technical design. The package should establish what the application feels like to use, with detailed implementation behaviour developed in technical design.
