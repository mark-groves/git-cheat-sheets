# 🧾 Git Commit Message Cheat Sheet (Conventional Commits)

## 📌 Format
```
<type>(<optional-scope>): <short summary>
```

**Example:**
```
feat(workflow): add retry logic for failed jobs
```

---

## ✅ Common Commit Types

| Type       | Purpose                                                                 |
|------------|-------------------------------------------------------------------------|
| `feat`     | A new feature                                                           |
| `fix`      | A bug fix                                                               |
| `docs`     | Changes to documentation only                                           |
| `style`    | Code style/formatting (whitespace, semicolons, etc. — no logic changes) |
| `refactor` | Code changes that neither fix a bug nor add a feature                  |
| `perf`     | Performance improvements                                                |
| `test`     | Adding or updating tests                                                |
| `build`    | Changes that affect the build system or external dependencies           |
| `ci`       | Changes to CI configuration files and scripts                          |
| `chore`    | Maintenance tasks (e.g. cleanup, deps, renames — no functional changes) |
| `revert`   | Reverts a previous commit                                               |

---

## 🧩 Common Scopes

| Scope         | Meaning                              |
|---------------|--------------------------------------|
| `workflow`    | Automation/workflow logic            |
| `email`       | Email content/templates              |
| `env`         | Environment variables or configs     |
| `deps`        | Dependencies                         |
| `auth`        | Authentication/auth logic            |
| `api`         | API-related logic                    |
| `infra`       | Infrastructure as code (IaC)         |
| `config`      | Config files (.env, YAML, JSON, etc) |
| `github-actions` | GitHub Actions workflows         |
| `docker`      | Docker files                         |
| `ui`          | User interface changes               |
| `scripts`     | Utility scripts                      |
| `docs`        | Docs content or doc tooling          |
| `monitoring`  | Logging, metrics, or alerts          |

---

## 🔥 Examples by Type

### `feat`
```bash
feat: add ability to pause workflows
feat(workflow): support dynamic retries based on error
feat(api): add endpoint for audit logging
```

### `fix`
```bash
fix: resolve null variable reference
fix(email): correct subject line in license report
fix(auth): token expiry check now consistent
```

### `docs`
```bash
docs: add README section for new module
docs(workflow): document variable usage
docs(email): clarify format of subject line
```

### `style`
```bash
style: format with Black & Prettier
style(workflow): align YAML spacing
```

### `refactor`
```bash
refactor: split long method into helpers
refactor(workflow): reuse shared steps
```

### `perf`
```bash
perf(api): reduce latency in report generation
perf(workflow): cache API token between steps
```

### `test`
```bash
test: add tests for new auth flow
test(workflow): mock variables for unit testing
```

### `build`
```bash
build: upgrade to Node 20
build(docker): optimise image layers
```

### `ci`
```bash
ci: add secrets to GitHub Actions
ci(github-actions): add caching to workflow
```

### `chore`
```bash
chore: rename internal variable for clarity
chore(workflow): clean up unused steps
chore(env): remove legacy config keys
```

### `revert`
```bash
revert: revert commit 3e21c9d - broke prod email flow
```

---

## 💣 Breaking Changes

Use `!` to indicate a breaking change:
```bash
feat(api)!: change output format to JSON
```

Include explanation in the body:
```
BREAKING CHANGE: This alters the response schema of /v1/report
```

---

## 🧪 Bonus: Emojis (Optional)

| Emoji | Type    | Example                                               |
|--------|---------|-------------------------------------------------------|
| ✨     | `feat`  | ✨ feat: add workflow toggling                        |
| 🐛     | `fix`   | 🐛 fix: prevent crash on empty workflow name         |
| 📝     | `docs`  | 📝 docs: update onboarding instructions              |
| 🎨     | `style` | 🎨 style: fix spacing in JSON config                 |
| ♻️     | `refactor` | ♻️ refactor: simplify retry logic               |
| 🔥     | n/a     | 🔥 remove dead code                                  |
| 🚀     | `build` | 🚀 build: bump Docker version                        |
| 🔧     | `chore` | 🔧 chore: tweak logging settings                     |
| ✅     | `test`  | ✅ test: add unit tests for input validation         |

---

## 🧠 Tips
- Limit subject line to **50 characters**
- Use **imperative mood** (“Add”, not “Added” or “Adds”)
- Wrap body at 72 characters (if longer message is needed)
- Skip full stops in subject lines

---