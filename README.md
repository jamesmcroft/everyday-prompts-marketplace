# everyday-prompts-marketplace

Everyday prompt skills for Copilot CLI - content writing, reviewing, social media, business ops, career growth, knowledge research, and dev workflows. Distributed as installable marketplace plugins.

## What's Here

| Directory | What it holds | Distribution |
|-----------|--------------|--------------|
| `plugins/` | Skills bundled as installable plugins | `copilot plugin install` |

## Quick Start

### Install from marketplace (VS Code UI)

1. Open **User Settings** (`Ctrl+,`)
2. Search for `marketplace` and click **Add Item** under **Github > Copilot > Chat > Agent Plugins > Marketplaces**
3. Enter: `jamesmcroft/everyday-prompts-marketplace`
4. Open the **Extensions** sidebar (`Ctrl+Shift+X`)
5. Type `@agentPlugins` in the search bar to browse available plugins
6. Click **Install** on the plugin you want

### Install from CLI session

```
/plugin marketplace add jamesmcroft/everyday-prompts-marketplace
/plugin install content-creator@everyday-prompts-marketplace
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| `content-creator` | Full content creation lifecycle - writing, reviewing, and promotion across blog, social, Pinterest, Instagram, and short-form video |
| `professional` | Day-to-day skills for knowledge workers - communication, planning, documentation, performance, and career development |
| `knowledge-research` | Iterative research orchestration and hypothesis generation |
| `developer` | Full development lifecycle - code review, PRs, build/test fixes, commits, issues, release notes, and codebase orientation |

## Related

These plugins are derived from the [everyday-prompts](https://github.com/jamesmcroft/everyday-prompts) collection. The original repo remains a reference for the underlying prompt patterns and templates.

## Contributing

### Add a skill to an existing plugin

1. Create `plugins/<plugin>/skills/<skill-name>/SKILL.md`
2. Follow the four-part structure: Role, Inputs, Instructions, Guidelines

### Create a new plugin

1. Create `plugins/<name>/plugin.json` (see existing plugins for format)
2. Add a `skills/` directory with at least one skill
3. Register it in `.github/plugin/marketplace.json`

## License

[MIT](LICENSE)
