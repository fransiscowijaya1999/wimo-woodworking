# Workshop Shelf Engineering Project

A modular timber shelving system for a motorcycle parts shop, designed in collaboration with Claude AI acting as a woodworking engineer.

## Project Overview

This repository contains:
- Complete design specifications for a 256cm × 50cm × 200cm modular wooden shelf system
- Claude AI project setup files (instructions, design state, reference data)
- Visual blueprints and sketches
- Vendor information and build progress logs
- Parts inventory organization plans

## Repository Structure

```
workshop-shelf-project/
│
├── 01-claude-project/      # Claude AI project setup files
├── 02-designs/             # Blueprints and sketches
├── 03-photos/              # Reference and progress photos
├── 04-vendors/             # Supplier and purchase info
├── 05-storage-planning/    # Inventory organization plans
└── 06-build-log/           # Dated progress journal
```

## Quick Start

### To use the Claude AI engineering assistant:

1. Open Claude.ai and create a new Project
2. Copy contents of `01-claude-project/WOODWORKING_ENGINEER_INSTRUCTIONS.md` into the Project Instructions field
3. Upload `01-claude-project/DESIGN_SPECIFICATIONS.md` and `01-claude-project/REFERENCE_DATA.md` as knowledge files
4. Start a chat — Claude will have full context of the design

### To contribute to the project:

1. Update `DESIGN_SPECIFICATIONS.md` when design decisions are made
2. Add dated entries to `06-build-log/` during construction
3. Save progress photos to `03-photos/` with descriptive names
4. Document new vendors in `04-vendors/`
5. Commit changes with descriptive messages (see git workflow below)

## Git Workflow

### Initial setup

```bash
git init
git add .
git commit -m "Initial commit: shelf design specifications"
```

### Connect to remote

```bash
git remote add origin <your-private-repo-url>
git branch -M main
git push -u origin main
```

### Ongoing workflow

```bash
# After making changes
git add .
git commit -m "Update bearing storage plan: added Tier 1 high-volume specs"
git push
```

### Commit message convention

Use prefixes for clarity:
- `Design:` — changes to design specifications
- `Build:` — construction progress updates
- `Storage:` — inventory organization changes
- `Vendor:` — supplier information updates
- `Docs:` — documentation improvements
- `Fix:` — corrections to errors

Example: `Design: Switched bearing cabinet to custom 50cm depth build`

## Image Handling

Photos and large files can bloat git repositories. Recommendations:

**Option 1: Compress images before committing**
- Use tools like ImageMagick to reduce file size
- Target: under 500KB per image where possible

**Option 2: Use Git LFS (Large File Storage)**
```bash
git lfs install
git lfs track "*.jpg" "*.png" "*.heic"
git add .gitattributes
```

**Option 3: Keep photos outside git**
- Store photos in cloud storage (Google Drive, etc.)
- Link from documentation files instead of embedding
- Add photos folder to `.gitignore`

## Privacy Notice

This repository has been **sanitized for public release**. The following categories of sensitive business information have been removed or generalized:
- Specific business location (district/village-level address)
- Competitive analysis (capital comparison against competitors)
- Vendor relationships (specific brand portfolio)
- Personal context about employees (mechanic count, operator details)

Only generic engineering content and region-level climate context (needed for wood-species and humidity decisions) remain.

⚠ **Note:** Git commit metadata (author name and email) is still part of the project history. If that is also a concern, scrub or rewrite history before publishing.

## Backup Strategy

Beyond git, consider:
- Cloud sync of working directory (Google Drive, Dropbox)
- Periodic ZIP archives of completed project milestones
- Photo backups separate from git (especially if not using LFS)

## License

No license is currently granted for reuse — all rights reserved by the maintainer.

The engineering principles and methodologies documented here are shared for reference only. If you intend to allow reuse, add an open-source license file and replace this section.

## Maintainer

[Your name/handle]
Kalimantan, Indonesia