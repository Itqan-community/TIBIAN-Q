<!--
SYNC IMPACT REPORT
==================
Version Change: (new constitution) → 1.0.0
Modified Principles: N/A (initial creation)
Added Sections:
  - Core Principles (5 principles defined)
  - Data Management Tools
  - Development Workflow
  - Governance
Removed Sections: N/A (initial creation)
Templates Requiring Updates:
  ✅ plan-template.md - references constitution check (no changes needed)
  ✅ spec-template.md - no constitution-specific constraints (no changes needed)
  ✅ tasks-template.md - aligns with TDD and branching strategy (no changes needed)
Follow-up TODOs: Update README.md with branching strategy hint
-->

# TIBIAN-Q Constitution

## Core Principles

### I. Obsidian-Driven Data Management
All project data, including maps of industry players, open source assets, and ITQAN products, MUST be managed through Obsidian. Data entry, editing, and organization SHALL be performed within the Obsidian environment. The project structure MUST remain compatible with Obsidian's markdown-based system and support its linking, tagging, and graph features.

**Rationale**: Obsidian provides a robust knowledge management system that allows for interconnected data representation, making it ideal for mapping complex relationships between Quranic technology entities. This ensures data consistency and leverages Obsidian's powerful features for visualization and navigation.

### II. Branch-Based Versioning Strategy
Each sub-map of the main Quranic Technologies Map (Industry Players, Open Source Assets, ITQAN Products) MUST have its own dedicated Git branch. Versioning and change management SHALL be performed through CLI or Git Bash commands. The main branch represents the integrated, stable state of all maps.

**Rationale**: Branch-based versioning enables parallel development of different map components while maintaining isolation and clear history. This approach supports independent evolution of each map while providing merge points for integration.

**Branch Naming Convention**:
- `main` - Integrated stable state
- `map/industry-players` - Industry Players Map
- `map/open-source-assets` - Open Source Assets Map
- `map/itqan-products` - ITQAN Products Map

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

**Required Metadata Fields** (YAML frontmatter in each map entry):
```yaml
---
name: [Entity Name]
category: [Category]
type: [industry-player|open-source|itqan-product]
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

4. **Commit changes**:
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

### Compliance and Review
- All pull requests MUST be reviewed for constitutional compliance
- Map quality reviews MUST be conducted quarterly
- Branch strategy and data quality metrics MUST be tracked
- Any proposed complexity additions MUST be justified against the simplicity principle

### Version Control
- Constitution uses semantic versioning: MAJOR.MINOR.PATCH
- MAJOR: Breaking changes to principles or workflow
- MINOR: New principles or significant guidance additions
- PATCH: Clarifications, corrections, minor updates

**Version**: 1.0.0 | **Ratified**: 2025-09-30 | **Last Amended**: 2025-09-30