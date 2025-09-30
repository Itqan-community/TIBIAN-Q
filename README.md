# TIBIAN-Q

TIBIAN Quranic Technologies Map

- Industry Players Map.
- Open Source Assets Map.
- ITQAN Products Map.

## Branching Strategy

This project uses a **branch-based versioning strategy** where each sub-map has its own dedicated branch:

- `main` - Integrated stable state of all maps
- `map/industry-players` - Industry Players Map development
- `map/open-source-assets` - Open Source Assets Map development
- `map/itqan-products` - ITQAN Products Map development

### Working with Maps

To work on a specific map:
```bash
# Switch to the map branch
git checkout map/[map-name]

# Make your changes in Obsidian

# Commit using conventional format
git add .
git commit -m "<type>(<scope>): <description>"

# Push changes
git push origin map/[map-name]
```

To integrate changes into main, create a pull request from the map branch.

For detailed workflow and governance, see [`.specify/memory/constitution.md`](.specify/memory/constitution.md).