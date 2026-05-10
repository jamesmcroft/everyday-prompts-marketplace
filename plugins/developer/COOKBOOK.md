# Developer Cookbook

Practical workflows and real-world examples for the `developer` plugin. These scenarios show how to use skills individually and how the agents chain them for end-to-end development workflows.

## Getting Started

```
/plugin marketplace add jamesmcroft/everyday-prompts-marketplace
/plugin install developer@everyday-prompts-marketplace
```

Once installed, invoke the `@dev` agent as your starting point. It classifies what you need and routes to the right domain agent.

---

## Workflow 1: Pick Up an Issue and Deliver

**Scenario:** You've been assigned issue #42 and want to work on it from start to finish.

**What to say:**

> Pick up issue #42.

**What happens:**

1. `@dev-planner` reads the issue, produces a summary (what, why, scope, risks), creates a branch, and updates the issue.
2. If the codebase is unfamiliar, `@dev-scout` runs an orientation first.
3. `@dev-engineer` takes over:
   - Plans the implementation with checkpoints.
   - Implements in small commits using the `/commit-message` skill.
   - Runs build and tests after each increment.
   - Self-reviews with the `/local-code-review` skill.
   - Publishes a PR with the `/pr-publish` skill.
   - Updates the issue with a link to the PR.

**One command starts the full lifecycle.** You approve at each checkpoint.

---

## Workflow 2: Review a Pull Request

**Scenario:** A teammate asks you to review their PR.

**What to say:**

> Review PR #15.

**What happens:**

1. `@dev-reviewer` fetches the PR: diff, description, CI status, linked issues.
2. Reviews file by file against priority categories: bugs, security, performance, incomplete changes, test coverage, simplification.
3. Drafts inline comments with severity and suggested fixes.
4. Presents all comments for your approval before posting.
5. After posting, offers to create follow-up issues for non-blocking problems found during review.

**For re-reviews** (after the author pushes updates):

> The author updated PR #15, re-review it.

The agent focuses on what changed since your last review while still considering the full context.

---

## Workflow 3: Fix a Broken Build

**Scenario:** CI is failing on your branch.

**What to say:**

> The build is failing.

**What happens:**

The `/build-fix` skill:

1. Identifies whether this is a local or CI failure.
2. Parses error messages and correlates them with your branch changes.
3. Classifies the failure (code error, dependency issue, config problem, or environment issue).
4. Traces to root cause through your diff.
5. Applies a fix, rebuilds, and runs tests.
6. Loops up to 3 times if the first fix doesn't resolve it.

If the failure is environmental (host issues, network problems), it reports the issue clearly and stops.

---

## Workflow 4: Fix Failing Tests

**Scenario:** You changed some code and now tests are failing.

**What to say:**

> Tests are failing.

**What happens:**

The `/test-fix` skill:

1. Runs the tests and parses which ones fail.
2. For each failing test, reads the test code AND the source under test.
3. Makes the key judgment: is the **test wrong** (expectations don't match legitimate behavior changes) or is the **code wrong** (a bug was introduced)?
4. Fixes the right thing: updates test assertions if behavior legitimately changed, or fixes the code if a bug was introduced.
5. Re-runs tests to validate.

This prevents the common mistake of blindly making tests pass without understanding what broke.

---

## Workflow 5: Ship Your Changes

**Scenario:** You've finished your implementation and want to create a PR.

**What to say:**

> Ship my changes.

**What happens:**

1. `@dev-engineer` runs a self-review using the `/local-code-review` skill:
   - Builds the code.
   - Runs tests.
   - Reviews the full branch diff for bugs, security issues, and incomplete changes.
   - Auto-fixes straightforward issues.
   - Reports complex findings.
2. Once clean, publishes a PR using the `/pr-publish` skill:
   - Generates a title and structured description from the diff.
   - Presents for your approval.
   - Pushes the branch and creates the PR.
3. Updates the issue with a link to the PR.

---

## Workflow 6: Understand a New Codebase

**Scenario:** You've been asked to contribute to a repo you've never worked in.

**What to say:**

> Help me understand this codebase.

**What happens:**

`@dev-scout` produces an orientation report:

- **Overview:** what the project is.
- **Tech stack:** languages, frameworks, build tools.
- **Architecture:** how the code is organized, key modules, data flow.
- **Key patterns:** conventions a contributor must follow.
- **Entry points:** where to start reading.
- **Complexity and risks:** areas that are complex, poorly tested, or carry tech debt.
- **Build and test:** how to build, run tests, and deploy.

You go from zero to productive without reading every file.

---

## Workflow 7: Create a Well-Structured Issue

**Scenario:** You spotted a problem during development and want to track it.

**What to say:**

> Create an issue: the user search API returns stale results when the cache TTL expires during a request. I noticed this while working on the search filters.

**What happens:**

The `/work-item-create` skill:

1. Analyzes the codebase to understand the search API and caching layer.
2. Checks for duplicate issues.
3. Generates a structured issue with context, requirements, expected functionality, and constraints.
4. Presents the draft for your approval.
5. Creates the issue and assigns it to you.

The specification is grounded in actual code, not generic descriptions.

---

## Workflow 8: Generate Release Notes

**Scenario:** You're publishing a new version and need release notes.

**What to say:**

> Generate release notes for v2.3.0. The previous version was v2.2.0.

**What happens:**

The `/release-notes` skill:

1. Gathers changes from the commit history between the two versions (or from a changelog you provide).
2. Categorizes into: New Features, Improvements, Bug Fixes, Breaking Changes, Deprecations.
3. Writes each entry in user-facing terms (what changed, why it matters, what to do for breaking changes).
4. Omits empty categories.

---

## Workflow 9: Commit with a Good Message

**Scenario:** You have staged changes and want a well-formatted commit message.

**What to say:**

> Commit these changes.

**What happens:**

The `/commit-message` skill:

1. Reads the staged diff.
2. Auto-detects the commit type (feat, fix, refactor, chore, docs, test, etc.).
3. Derives the scope from the affected area.
4. Writes an imperative subject line under 72 characters.
5. Adds a body only when the "why" isn't obvious from the subject.
6. Shows the message for your confirmation before committing.

---

## Tips

- **Start with `@dev`** for anything you're not sure how to phrase. It routes to the right agent.
- **The full lifecycle flow** (pick up issue, implement, ship) handles everything. You just approve at checkpoints.
- **Test fix distinguishes broken tests from broken code.** This is its most valuable feature. Trust its diagnosis, but verify.
- **Self-review before PR** catches things you'd be embarrassed to have a reviewer find. Always run it.
- **Scout before contributing** to unfamiliar repos. The orientation report saves hours of "where do I even start?"
- **Commit messages are generated from the actual diff**, not guessed from file names. The more focused your staged changes, the better the message.
