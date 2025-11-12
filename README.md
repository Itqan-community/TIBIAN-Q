# TIBIAN-Q

TIBIAN Quranic Technologies Map

- Industry Players Map.
- Open Source Assets Map.
- ITQAN Products Map.
- Quran Apps Directory Map.
- ITQAN Human Resources Map.
- Quranic Apps Features Map.

## How It Works

This project uses **automated governance** to maintain consistency across all documentation and branches:

### ✨ Key Automation Features

1. **Automatic Protocol Propagation** (Constitution Principle VI)
   - When you add a new map to this README, the system automatically:
     - Updates the constitution with the new map reference
     - Creates the corresponding Git branch (`map/[new-map-name]`)
     - Pushes the new branch to remote
     - Updates all relevant specs and documentation

2. **Automatic Commits** (Constitution Principle VII)
   - Governance changes (constitution, README, specs) are automatically committed
   - No need to manually run `git add` and `git commit` for governance files
   - You retain full control over pushing, merging, and creating PRs

3. **Branch Protection**
   - Only predefined map branches are allowed
   - LLM agents cannot create arbitrary branches
   - All branches follow the naming convention: `map/[map-name]`

### 🗺️ Branching Strategy

This project uses a **branch-based versioning strategy** where each sub-map has its own dedicated branch:

- `main` - Integrated stable state of all maps
- `map/industry-players` - Industry Players Map development
- `map/open-source-assets` - Open Source Assets Map development
- `map/itqan-products` - ITQAN Products Map development
- `map/quran-apps-directory` - Quran Apps Directory Map development
- `ITQAN-human-resources` - ITQAN Human Resources Map development
- `map/quranic-apps-features` - Quranic Apps Features Map development

## Working with Maps

### Day-to-Day Map Editing

To work on a specific map:
```bash
# 1. Switch to the map branch
git checkout map/[map-name]

# 2. Make your changes in Obsidian
#    - Add/edit entries with required metadata
#    - Create cross-references using wikilinks
#    - Tag appropriately

# 3. Commit using conventional format
git add .
git commit -m "<type>(<scope>): <description>"

# Examples:
# git commit -m "add(industry-players): add Quran.com as industry player"
# git commit -m "update(open-source): update Tanzil project metadata"

# 4. Push changes
git push origin map/[map-name]
```

### Adding a New Map (Triggers Automation!)

When you need to add a new sub-map to the project:

```bash
# 1. Add the new map to this README.md (in the list at the top)
#    For example: "- Tafsir Resources Map."

# 2. The automatic protocol propagation will:
#    ✅ Update constitution with new map reference
#    ✅ Create git branch: map/tafsir-resources
#    ✅ Push new branch to remote
#    ✅ Update relevant specs
#    ✅ Auto-commit all changes

# 3. Switch to the new branch and initialize structure in Obsidian
git checkout map/tafsir-resources
# Then create your first entries in Obsidian
```

### Reviewing Auto-Commits

All automatic commits are visible in git history and can be reviewed or reverted:

```bash
# View recent commits (including auto-commits)
git log --oneline -10

# See what changed in an auto-commit
git show <commit-hash>

# Revert an auto-commit if needed
git revert <commit-hash>
```

### Integrating Changes to Main

To integrate changes into main, create a pull request from the map branch:

```bash
# Ensure your map branch is up to date
git checkout map/[map-name]
git merge main
git push origin map/[map-name]

# Then create PR on GitHub from map/[map-name] to main
```

## Troubleshooting

### I accidentally committed to the wrong branch
```bash
# If you haven't pushed yet:
git reset --soft HEAD~1  # Undo commit, keep changes
git checkout map/correct-branch
git add .
git commit -m "your message"
```

### I want to switch branches but have uncommitted changes
```bash
# Option 1: Commit your changes first
git add .
git commit -m "wip: work in progress"
git checkout map/other-branch

# Option 2: Stash your changes
git stash
git checkout map/other-branch
# Later: git stash pop
```

### How do I know which branch I'm on?
```bash
git branch  # Shows all branches, * marks current
git status  # Shows current branch and file status
```

## Documentation

- **Constitution**: [`.specify/memory/constitution.md`](.specify/memory/constitution.md) - Core principles including automation features
- **Feature Spec**: [`specs/001-teach-people-how/spec.md`](specs/001-teach-people-how/spec.md) - Comprehensive guide to the workflow
- **Obsidian Setup**: Use Obsidian v1.0+ to manage map data with markdown, wikilinks, and graph view