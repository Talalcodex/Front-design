# front-design

A Claude Skill that turns Claude into a world-class UI/UX design engineer: senior product designer, creative director, motion designer, responsive specialist and frontend engineer in one.

## What it does

`front-design` enforces a workflow that avoids generic AI-looking interfaces:

1. **Brief**: identify product category, audience, platform and constraints.
2. **Research**: study the current design landscape (Awwwards, Dribbble, Behance, Godly, SiteInspire, Land-book, Mobbin and others) before designing. If browsing is unavailable, Claude says so and asks for references.
3. **Three concepts**: three distinct design directions, each with a real visual preview (interactive HTML, React, or rendered screenshots), including a mobile layout.
4. **Stop**: you pick A, B or C, request changes, combine concepts, or ask for a new set. Nothing is built until you approve.
5. **Build**: design spec, architecture, implementation, animation, responsive work, QA and polish.
6. **Deliver**: runnable project, source, docs, setup instructions and honest limitations.

Covers websites, SaaS, dashboards, admin panels, landing pages, e-commerce, education, healthcare, portfolios, social, AI apps, mobile apps and PWAs.

## Repository layout

```
front-design/
├── README.md
├── LICENSE
├── .gitignore
└── front-design/
    ├── SKILL.md
    └── references/
        ├── design-research-methodology.md
        ├── modern-ui-patterns.md
        ├── animation-guidelines.md
        ├── frontend-development-standards.md
        ├── responsive-design-checklist.md
        ├── accessibility-and-performance.md
        └── quality-assurance-checklist.md
```

`SKILL.md` holds the core workflow. The `references/` files are loaded only when needed (progressive disclosure).

## Installation

### Claude.ai (web, desktop, mobile)

1. Download `front-design.zip` (or zip the inner `front-design/` folder yourself so that `SKILL.md` sits inside a `front-design/` folder in the archive).
2. Open **Settings > Capabilities** (or **Customize > Skills**, depending on your plan and version).
3. Enable Skills, then upload the zip as a custom skill.
4. Turn the skill on and start a new chat.

Availability of custom skills depends on your plan and organization settings.

### Claude Code

Personal (all projects):

```bash
mkdir -p ~/.claude/skills
cp -r front-design ~/.claude/skills/
```

Project only:

```bash
mkdir -p .claude/skills
cp -r front-design .claude/skills/
```

Restart or reload Claude Code so it discovers the skill.

## Usage

Just describe what you want:

- "Build a landing page for my AI note-taking app."
- "Design a dashboard for a physiotherapy clinic."
- "Redesign my portfolio so it feels less like a template."

Claude will research, show three concepts, and wait for your choice before building.

## Customizing

- Edit the `description` in `SKILL.md` to change when the skill triggers.
- Add or modify files in `references/` to encode your own brand rules, preferred stack or component library.
- Keep `SKILL.md` focused; put long material in `references/`.

## Requirements and limits

- Web research needs a browsing or search tool. Without it, the skill discloses the limitation and asks for references.
- Live previews depend on the environment (artifacts, file tools, or local files).
- Automated audits (Lighthouse, axe) run only if the environment has the tooling; results are reported honestly.

## Contributing

Issues and pull requests are welcome. Keep instructions non-contradictory, keep `SKILL.md` under about 500 lines, and make sure every referenced file exists.

## License

MIT. See `LICENSE`.
