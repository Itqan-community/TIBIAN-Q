# Feature Specification: Comprehensive User Guide for Automated Governance Workflow

**Feature Branch**: `001-teach-people-how`
**Created**: 2025-09-30
**Status**: Updated
**Input**: User description: "teach people how they can commit only the branch if they are using CLI in managing their changes. Also force the protection where the LLM don't create branches as it likes. We only create branch if we needed and work with branches is constrained by sub map which is a sub project of the main project. Add everything to the 001 to teach user how to use this including automatic protocol propagation, automatic commits, and automatic branch creation."

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
As a contributor managing Quranic Technologies Map data (including Industry Players, Open Source Assets, ITQAN Products, Quran Apps Directory, ITQAN Community Organizational Chart, and Quranic Apps Features) through Obsidian and CLI, I need comprehensive guidance on:
1. How to commit changes only to my current map branch without accidentally affecting other branches
2. How the automatic protocol propagation works when adding new maps
3. How automatic commits work for governance documents
4. How automatic branch creation happens when new maps are added
5. What branch creation restrictions exist for LLMs and why

As a project maintainer, I need documentation that clearly explains the entire automated governance workflow, including automatic protocol propagation (Constitution Principle VI), automatic commits (Principle VII), and branch constraints, so that all contributors understand how the system maintains consistency automatically.

### Acceptance Scenarios
1. **Given** a contributor is working on the Industry Players map, **When** they commit changes via CLI, **Then** only the `map/industry-players` branch is updated and no other branches are affected
2. **Given** a user adds a new map to README.md, **When** the automatic protocol propagation triggers, **Then** constitution is updated, branch is created, spec is updated, and all changes are auto-committed
3. **Given** an LLM updates constitution or README, **When** the changes are completed, **Then** the system automatically commits the changes with proper conventional commit message and attribution
4. **Given** a new map branch is needed, **When** the protocol propagation runs, **Then** the corresponding Git branch is automatically created and pushed to remote
5. **Given** an LLM is assisting with documentation or data entry, **When** the LLM attempts to create a new branch, **Then** the system prevents the creation unless explicitly authorized by a human maintainer
6. **Given** a contributor needs to work on a different map, **When** they switch branches via CLI, **Then** they receive confirmation of the current branch and guidance on proper commit workflow
7. **Given** a new contributor joins the project, **When** they read the documentation, **Then** they understand the branch structure, commit workflow, automation features, and constraints clearly
8. **Given** an LLM is operating within the project, **When** it needs to make changes, **Then** it follows the branch constraints and does not create new branches outside the predefined sub-map structure

### Edge Cases
- What happens when a contributor accidentally tries to commit to main directly?
- How does the system handle merge conflicts between map branches?
- What happens if someone tries to create a branch with a non-standard name?
- How do we handle emergency fixes that might require a hotfix branch?
- What happens when an LLM suggests creating a feature branch for a sub-map enhancement?

## Requirements *(mandatory)*

### Functional Requirements

**Documentation Requirements**:
- **FR-001**: README.md MUST provide clear CLI commit guidelines showing how to commit only to current branch
- **FR-002**: README.md MUST include step-by-step examples for common CLI workflows (commit, push, branch switching)
- **FR-003**: README.md MUST clearly state all allowed map branches and their purposes
- **FR-004**: README.md MUST include troubleshooting section for common branch-related mistakes
- **FR-005**: README.md MUST explain automatic protocol propagation feature (Constitution Principle VI)
- **FR-006**: README.md MUST explain automatic commit feature (Constitution Principle VII)
- **FR-007**: README.md MUST explain automatic branch creation when new maps are added
- **FR-008**: README.md MUST include "How It Works" section explaining the automation workflow

**Branch Policy Requirements**:
- **FR-009**: Constitution MUST explicitly define the allowed branch structure (main + map branches)
- **FR-010**: Constitution MUST include principle prohibiting arbitrary branch creation by LLMs
- **FR-011**: Constitution MUST specify when new branches are allowed (only by human maintainers or automatic protocol)
- **FR-012**: Documentation MUST include LLM behavioral constraints regarding branch operations

**Automation Requirements**:
- **FR-013**: Documentation MUST explain that governance changes are automatically committed
- **FR-014**: Documentation MUST explain scope of auto-commits (constitution, README, specs)
- **FR-015**: Documentation MUST explain what remains under user control (push, merge, PRs)
- **FR-016**: Documentation MUST explain how to review and revert auto-commits if needed
- **FR-017**: Documentation MUST explain automatic branch creation and push when maps are added
- **FR-018**: Documentation MUST explain protocol propagation across all governance documents

**Workflow Requirements**:
- **FR-019**: CLI workflow MUST ensure commits target only the current checked-out branch
- **FR-020**: Documentation MUST show how to verify current branch before committing
- **FR-021**: Documentation MUST provide commands for safe branch switching without affecting other branches
- **FR-022**: Documentation MUST include guidance on branch synchronization with main
- **FR-023**: Documentation MUST provide workflow for adding new maps (trigger propagation)

**Protection Requirements**:
- **FR-024**: System MUST communicate branch creation restrictions to LLM agents through constitution and agent-specific guidance files
- **FR-025**: Documentation MUST include examples of correct vs. incorrect branch operations

### Key Entities *(include if feature involves data)*

- **Map Branch**: One of the predefined branches (map/industry-players, map/open-source-assets, map/itqan-products, map/quran-apps-directory, map/itqan-community-org-chart, map/quranic-apps-features) representing a sub-map of the main Quranic Technologies Map
- **Main Branch**: The integrated, stable state of all maps; protected from direct commits
- **CLI Workflow**: The sequence of git commands used to check branch status, switch branches, commit changes, and push updates
- **LLM Agent**: An AI assistant operating within the project that must respect branch constraints and not create branches autonomously
- **Branch Policy**: The set of rules defined in the constitution governing when and how branches can be created and modified
- **Automatic Protocol Propagation**: System feature (Principle VI) that automatically updates all governance documents and creates branches when new maps are added
- **Automatic Commit**: System feature (Principle VII) that automatically commits governance changes without manual git commands
- **Governance Documents**: Constitution, README, and specs that are subject to automatic commits and propagation

---

## Review & Acceptance Checklist
*GATE: Automated checks run during main() execution*

### Content Quality
- [x] No implementation details (languages, frameworks, APIs)
- [x] Focused on user value and business needs
- [x] Written for non-technical stakeholders
- [x] All mandatory sections completed

### Requirement Completeness
- [x] No [NEEDS CLARIFICATION] markers remain (removed pre-commit hooks - using automatic commits instead)
- [x] Requirements are testable and unambiguous
- [x] Success criteria are measurable
- [x] Scope is clearly bounded
- [x] Dependencies and assumptions identified

---

## Execution Status
*Updated by main() during processing*

- [x] User description parsed (updated with automation features)
- [x] Key concepts extracted (including automatic propagation and commits)
- [x] Ambiguities resolved (pre-commit hooks replaced with automatic commits)
- [x] User scenarios defined (8 scenarios including automation)
- [x] Requirements generated (25 requirements across 5 categories)
- [x] Entities identified (8 entities including automation features)
- [x] Review checklist passed (all items complete)

---