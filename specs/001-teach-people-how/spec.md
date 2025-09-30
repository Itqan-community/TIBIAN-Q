# Feature Specification: CLI Branch Management and Commit Guidelines

**Feature Branch**: `001-teach-people-how`
**Created**: 2025-09-30
**Status**: Draft
**Input**: User description: "teach people how they can commit only the branch if they are using CLI in manaing their changes. Also force the protection where the LLM don't create branches as it likes. We only create branch if we needed and work with branches is constrained by sub map which is a sub project of the main project."

## Execution Flow (main)
```
1. Parse user description from Input
   → If empty: ERROR "No feature description provided"
2. Extract key concepts from description
   → Identify: actors, actions, data, constraints
3. For each unclear aspect:
   → Mark with [NEEDS CLARIFICATION: specific question]
4. Fill User Scenarios & Testing section
   → If no clear user flow: ERROR "Cannot determine user scenarios"
5. Generate Functional Requirements
   → Each requirement must be testable
   → Mark ambiguous requirements
6. Identify Key Entities (if data involved)
7. Run Review Checklist
   → If any [NEEDS CLARIFICATION]: WARN "Spec has uncertainties"
   → If implementation details found: ERROR "Remove tech details"
8. Return: SUCCESS (spec ready for planning)
```

---

## ⚡ Quick Guidelines
- ✅ Focus on WHAT users need and WHY
- ❌ Avoid HOW to implement (no tech stack, APIs, code structure)
- 👥 Written for business stakeholders, not developers

### Section Requirements
- **Mandatory sections**: Must be completed for every feature
- **Optional sections**: Include only when relevant to the feature
- When a section doesn't apply, remove it entirely (don't leave as "N/A")

### For AI Generation
When creating this spec from a user prompt:
1. **Mark all ambiguities**: Use [NEEDS CLARIFICATION: specific question] for any assumption you'd need to make
2. **Don't guess**: If the prompt doesn't specify something (e.g., "login system" without auth method), mark it
3. **Think like a tester**: Every vague requirement should fail the "testable and unambiguous" checklist item
4. **Common underspecified areas**:
   - User types and permissions
   - Data retention/deletion policies
   - Performance targets and scale
   - Error handling behaviors
   - Integration requirements
   - Security/compliance needs

---

## User Scenarios & Testing *(mandatory)*

### Primary User Story
As a contributor managing Quranic Technologies Map data through Obsidian and CLI, I need clear guidance on how to commit changes only to my current map branch without accidentally affecting other branches or creating unnecessary branches. As a project maintainer, I need to enforce branch creation policies that prevent LLMs from creating branches arbitrarily and ensure all branch work aligns with the defined sub-map structure (industry-players, open-source-assets, itqan-products, quran-apps-directory).

### Acceptance Scenarios
1. **Given** a contributor is working on the Industry Players map, **When** they commit changes via CLI, **Then** only the `map/industry-players` branch is updated and no other branches are affected
2. **Given** an LLM is assisting with documentation or data entry, **When** the LLM attempts to create a new branch, **Then** the system prevents the creation unless explicitly authorized by a human maintainer
3. **Given** a contributor needs to work on a different map, **When** they switch branches via CLI, **Then** they receive confirmation of the current branch and guidance on proper commit workflow
4. **Given** a new contributor joins the project, **When** they read the documentation, **Then** they understand the branch structure, commit workflow, and constraints clearly
5. **Given** an LLM is operating within the project, **When** it needs to make changes, **Then** it follows the branch constraints and does not create new branches outside the predefined sub-map structure

### Edge Cases
- What happens when a contributor accidentally tries to commit to main directly?
- How does the system handle merge conflicts between map branches?
- What happens if someone tries to create a branch with a non-standard name?
- How do we handle emergency fixes that might require a hotfix branch?
- What happens when an LLM suggests creating a feature branch for a sub-map enhancement?

## Requirements *(mandatory)*

### Functional Requirements

**Documentation Requirements**:
- **FR-001**: System MUST provide clear CLI commit guidelines in README.md showing how to commit only to current branch
- **FR-002**: Documentation MUST include step-by-step examples for common CLI workflows (commit, push, branch switching)
- **FR-003**: Documentation MUST clearly state the four allowed map branches and their purposes
- **FR-004**: Documentation MUST include troubleshooting section for common branch-related mistakes

**Branch Policy Requirements**:
- **FR-005**: Constitution MUST explicitly define the allowed branch structure (main + 4 map branches only)
- **FR-006**: Constitution MUST include principle prohibiting arbitrary branch creation by LLMs
- **FR-007**: Constitution MUST specify when new branches are allowed (only by human maintainers for specific needs)
- **FR-008**: Documentation MUST include LLM behavioral constraints regarding branch operations

**Workflow Requirements**:
- **FR-009**: CLI workflow MUST ensure commits target only the current checked-out branch
- **FR-010**: Documentation MUST show how to verify current branch before committing
- **FR-011**: Documentation MUST provide commands for safe branch switching without affecting other branches
- **FR-012**: Documentation MUST include guidance on branch synchronization with main

**Protection Requirements**:
- **FR-013**: System MUST communicate branch creation restrictions to LLM agents through constitution and agent-specific guidance files
- **FR-014**: Documentation MUST include examples of correct vs. incorrect branch operations
- **FR-015**: System MUST provide pre-commit hooks or validation to prevent commits to main [NEEDS CLARIFICATION: should direct commits to main be blocked via git hooks?]

### Key Entities *(include if feature involves data)*

- **Map Branch**: One of four predefined branches (map/industry-players, map/open-source-assets, map/itqan-products, map/quran-apps-directory) representing a sub-map of the main Quranic Technologies Map
- **Main Branch**: The integrated, stable state of all maps; protected from direct commits
- **CLI Workflow**: The sequence of git commands used to check branch status, switch branches, commit changes, and push updates
- **LLM Agent**: An AI assistant operating within the project that must respect branch constraints and not create branches autonomously
- **Branch Policy**: The set of rules defined in the constitution governing when and how branches can be created and modified

---

## Review & Acceptance Checklist
*GATE: Automated checks run during main() execution*

### Content Quality
- [x] No implementation details (languages, frameworks, APIs)
- [x] Focused on user value and business needs
- [x] Written for non-technical stakeholders
- [x] All mandatory sections completed

### Requirement Completeness
- [ ] No [NEEDS CLARIFICATION] markers remain (1 present - pre-commit hooks decision)
- [x] Requirements are testable and unambiguous
- [x] Success criteria are measurable
- [x] Scope is clearly bounded
- [x] Dependencies and assumptions identified

---

## Execution Status
*Updated by main() during processing*

- [x] User description parsed
- [x] Key concepts extracted
- [x] Ambiguities marked (1 clarification needed)
- [x] User scenarios defined
- [x] Requirements generated
- [x] Entities identified
- [x] Review checklist passed (with 1 clarification pending)

---