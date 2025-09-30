<!--
SYNC IMPACT REPORT
==================
Version Change: 1.1.0 → 1.1.1
Modified Principles:
  - Principle VI: Automatic Protocol Propagation - added automatic Git branch creation requirement
Added Sections: N/A (patch update)
Removed Sections: N/A
Templates Requiring Updates:
  ✅ plan-template.md - no changes needed
  ✅ spec-template.md - no changes needed
  ✅ tasks-template.md - no changes needed
  ✅ README.md - no changes needed
  ⚠ .specify/scripts/ - requires update to support automatic branch creation
Follow-up TODOs:
  - Implement automation script to create and push Git branches when maps are added
  - Update protocol propagation script to include branch creation logic
  - Implement auto-commit functionality for governance updates
-->

# TIBIAN-Q Constitution

## Core Principles

### I. Obsidian-Driven Data Management
All project data, including maps of industry players, open source assets, ITQAN products, and Quran apps directory, MUST be managed through Obsidian. Data entry, editing, and organization SHALL be performed within the Obsidian environment. The project structure MUST remain compatible with Obsidian's markdown-based system and support its linking, tagging, and graph features.

**Rationale**: Obsidian provides a robust knowledge management system that allows for interconnected data representation, making it ideal for mapping complex relationships between Quranic technology entities. This ensures data consistency and leverages Obsidian's powerful features for visualization and navigation.

### II. Branch-Based Versioning Strategy
Each sub-map of the main Quranic Technologies Map (Industry Players, Open Source Assets, ITQAN Products, Quran Apps Directory) MUST have its own dedicated Git branch. Versioning and change management SHALL be performed through CLI or Git Bash commands. The main branch represents the integrated, stable state of all maps.

**Rationale**: Branch-based versioning enables parallel development of different map components while maintaining isolation and clear history. This approach supports independent evolution of each map while providing merge points for integration.

**Branch Naming Convention**:
- `main` - Integrated stable state
- `map/industry-players` - Industry Players Map
- `map/open-source-assets` - Open Source Assets Map
- `map/itqan-products` - ITQAN Products Map
- `map/quran-apps-directory` - Quran Apps Directory Map

### III. Documentation-First Approach
All features, changes, and architectural decisions MUST be documented before implementation. Documentation SHALL be written in Markdown format and stored within the `.specify/` directory structure. Changes to maps MUST include clear commit messages describing what entities were added, modified, or removed.

**Rationale**: Documentation-first ensures that all stakeholders understand the purpose and scope of changes before they are made. For a mapping project, this is crucial for maintaining data quality and consistency.

### IV. Atomic Commits and Clear History
Each commit MUST represent a single logical change (e.g., adding one company, updating one technology entry). Commit messages MUST follow the convention: `<type>(<scope>): <description>` where type is one of: `add`, `update`, `remove`, `docs`, `fix`, `refactor`.

**Examples**:
- `add(industry-players): add Quran.com as industry player`
- `update(open-source): update Tanzil project metadata`
- `remove(itqan-products): remove deprecated ITQAN Reader`

**Rationale**: Atomic commits create a clear, navigable history that makes it easy to understand what changed, when, and why. This is essential for collaborative mapping projects where multiple contributors may be working on different areas.

### V. Data Quality and Validation
All map entries MUST include required metadata fields (name, category, description, relationships). Before merging any map branch to main, validation MUST be performed to ensure data completeness and correctness. Broken links, missing required fields, and inconsistent categorization MUST be resolved before merge.

**Rationale**: High data quality is non-negotiable for a reference map. Enforcing validation ensures that the maps remain useful and reliable for all stakeholders.

### VI. Automatic Protocol Propagation
When a new sub-map is added to the project (e.g., added to README.md), the protocol MUST automatically propagate updates across all governance documents AND create the corresponding Git branch. This includes:
- Constitution MUST be updated with the new map branch reference
- README.md MUST reflect the new branch in branching strategy
- All feature specifications referencing map structure MUST be updated
- Branch naming conventions MUST be automatically extended
- Corresponding Git branch MUST be automatically created and pushed to remote

**Rationale**: Manual propagation of map additions across multiple documents is error-prone and creates inconsistency. Automatic propagation ensures that all governance artifacts remain synchronized and reduces cognitive overhead for maintainers. This principle enforces the DRY (Don't Repeat Yourself) principle at the governance level. Automatic branch creation ensures the branch structure stays in sync with the documented map structure, eliminating the possibility of missing branches.

**Implementation Requirements**:
- Detection mechanism to identify when README.md map list changes
- Automated script to update constitution, specs, and templates
- Automated Git branch creation with naming convention: `map/[map-name]`
- Automatic push of new branch to remote repository
- Validation to ensure all references and branches are created consistently

### VII. Streamlined Commit Workflow
Governance changes (constitution updates, README updates, spec updates) MUST be automatically committed without requiring explicit commit commands. When governance documents are updated through automated processes or LLM assistance, the system MUST:
- Stage all governance file changes automatically
- Generate appropriate conventional commit messages
- Commit changes with proper attribution
- Provide commit confirmation to the user

**Rationale**: Requiring manual commits for every governance change creates friction and interrupts workflow. Since governance updates follow strict patterns and conventions, they can be safely automated. This reduces cognitive load and ensures consistency in commit messages while maintaining full audit trail through git history.

**Scope**:
- Applies to: `.specify/memory/constitution.md`, `README.md`, `specs/*/spec.md`
- Does NOT apply to: Data files, implementation code, or user-facing content
- User MUST retain explicit control over: Pushing to remote, merging branches, creating PRs

**Safety Constraints**:
- Auto-commit only occurs when validation passes
- Changes must be reviewable via `git log` and `git diff`
- User can revert auto-commits using standard git commands
- Auto-commit messages must clearly indicate automation source

## Data Management Tools

**Primary Tool**: Obsidian (v1.0+)
- Markdown-based note system
- Graph view for relationship visualization
- Tagging and metadata support
- Cross-referencing via wikilinks

**Version Control**: Git via CLI or Git Bash
- Branch-based workflow for each sub-map
- Conventional commit messages
- Pull request workflow for merging to main
- Automated governance commits (Principle VII)

**Required Metadata Fields** (YAML frontmatter in each map entry):
```yaml
---
name: [Entity Name]
category: [Category]
type: [industry-player|open-source|itqan-product|quran-apps-directory]
status: [active|deprecated|archived]
url: [Primary URL if applicable]
description: [Brief description]
tags: [list, of, relevant, tags]
related: [[Link to Related Entities]]
---
```

## Development Workflow

### Adding or Updating Map Entries

1. **Switch to appropriate branch**:
   ```bash
   git checkout map/[map-name]
   ```

2. **Open Obsidian and make changes**:
   - Add/edit entries using Obsidian interface
   - Ensure all required metadata fields are filled
   - Create cross-references using wikilinks
   - Tag appropriately

3. **Validate changes**:
   - Review in Obsidian graph view for relationship correctness
   - Check for broken links
   - Verify metadata completeness

4. **Commit changes** (automatic for governance, manual for data):
   ```bash
   git add .
   git commit -m "<type>(<scope>): <description>"
   ```

5. **Push to remote**:
   ```bash
   git push origin map/[map-name]
   ```

6. **Create pull request to merge to main** (when ready to integrate):
   - PR must include summary of changes
   - Data quality validation must pass
   - At least one reviewer approval required

### Adding a New Sub-Map

When adding a new sub-map to the project:

1. **Update README.md** with the new map name in the list
2. **Trigger automatic protocol propagation** (Principle VI):
   - Constitution is automatically updated
   - Branch naming conventions are extended
   - Relevant specs are updated
   - Git branch `map/[new-map-name]` is automatically created
   - New branch is automatically pushed to remote
   - Changes are auto-committed (Principle VII)
3. **Initialize map structure in Obsidian** on the new branch

**Note**: The map branch creation and push (formerly step 3) is now automated as part of the protocol propagation in step 2.

### Branch Synchronization

Periodically synchronize map branches with main to incorporate changes from other maps:
```bash
git checkout map/[map-name]
git merge main
git push origin map/[map-name]
```

## Governance

### Constitution Authority
This constitution supersedes all other development practices. Any deviation MUST be explicitly documented with justification in the relevant specification or plan document.

### Amendment Process
Amendments to this constitution require:
1. Proposed change documented with rationale
2. Impact analysis on existing workflows and data
3. Approval from project maintainers
4. Migration plan for existing data/processes if needed
5. Version increment following semantic versioning rules
6. Automatic propagation of changes to dependent documents (Principle VI)

### Compliance and Review
- All pull requests MUST be reviewed for constitutional compliance
- Map quality reviews MUST be conducted quarterly
- Branch strategy and data quality metrics MUST be tracked
- Any proposed complexity additions MUST be justified against the simplicity principle
- Automated governance updates MUST be reviewed in quarterly audits

### Version Control
- Constitution uses semantic versioning: MAJOR.MINOR.PATCH
- MAJOR: Breaking changes to principles or workflow
- MINOR: New principles or significant guidance additions
- PATCH: Clarifications, corrections, minor updates

**Version**: 1.1.1 | **Ratified**: 2025-09-30 | **Last Amended**: 2025-09-30