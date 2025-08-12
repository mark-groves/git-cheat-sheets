# 🧾 Git Commit Message Cheat Sheet (Conventional Commits)

## 📑 Table of Contents
- [Quick Reference](#-quick-reference)
- [Format](#-format)
- [Common Commit Types](#-common-commit-types)
- [Common Scopes](#-common-scopes)
- [Examples by Type](#-examples-by-type)
- [Breaking Changes](#-breaking-changes)
- [Multi-line Commits](#-multi-line-commits)
- [Co-authored Commits](#-co-authored-commits)
- [Common Workflows](#-common-workflows)
- [Anti-patterns](#-anti-patterns)
- [Commit Message Guidelines](#-commit-message-guidelines)
- [Git Hooks](#-git-hooks)
- [Bonus: Emojis](#-bonus-emojis-optional)
- [Reference Links](#-reference-links)

---

## ⚡ Quick Reference

### Basic Format
```
<type>(<scope>): <description>

<body>

<footer>
```

### Key Rules
- **Subject line**: 50 characters max, imperative mood, no period
- **Body**: 72 characters per line, explain *what* and *why*
- **Footer**: Reference issues, breaking changes, co-authors

### Most Common Types
- `feat`: ✨ New feature
- `fix`: 🐛 Bug fix  
- `docs`: 📝 Documentation
- `refactor`: ♻️ Code restructure
- `test`: ✅ Tests
- `chore`: 🔧 Maintenance

---

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
| `security` | Security improvements or vulnerability fixes                            |
| `hotfix`   | Critical fixes for production issues                                    |
| `wip`      | Work in progress (temporary commits, usually squashed later)            |
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

### `security`
```bash
security: fix SQL injection vulnerability in user input
security(auth): update password hashing algorithm
security(api): sanitize user input in search endpoint
```

### `hotfix`
```bash
hotfix: critical fix for payment processing error
hotfix(api): resolve null pointer in checkout flow
```

### `wip`
```bash
wip: exploring new notification system
wip(ui): rough draft of new dashboard layout
```

---

## 💣 Breaking Changes

Use `!` to indicate a breaking change:
```bash
feat(api)!: change output format to JSON
```

### Full Format with Body and Footer
```bash
feat(api)!: change report output format to JSON

Previous XML format is deprecated and will be removed in v3.0.
New format provides better performance and easier parsing.

BREAKING CHANGE: The /v1/report endpoint now returns JSON instead of XML.
Update your client code to parse JSON responses.

Closes #123
```

### Breaking Change in Footer Only
```bash
refactor(database): optimize user query performance

Improve query speed by 80% through better indexing
and query restructuring.

BREAKING CHANGE: user.getAll() method signature changed
from getAll(limit) to getAll(options)
```

---

## 📄 Multi-line Commits

Use longer commits for complex changes that need explanation:

### Feature with Body
```bash
feat(auth): implement OAuth2 integration

Add support for Google and GitHub OAuth2 providers.
This includes token refresh logic and user profile
synchronization. Fallback to local auth remains available.

Closes #245
Refs #190
```

### Bug Fix with Body
```bash
fix(payment): resolve race condition in checkout

Payment processor was sometimes called twice when users
double-clicked the submit button. Added debouncing and
state management to prevent duplicate transactions.

The fix includes:
- Button state management
- Request deduplication
- Error handling improvements

Fixes #456
```

### Refactor with Detailed Explanation
```bash
refactor(api): extract user validation into middleware

Move user validation logic from individual controllers
into reusable middleware. This reduces code duplication
and makes validation consistent across all endpoints.

Changes:
- Create validateUser middleware
- Update all user-related controllers
- Add comprehensive validation tests
- Update API documentation

No functional changes to existing behavior.
```

---

## 👥 Co-authored Commits

Use when working with others (pair programming, collaboration):

### Single Co-author
```bash
feat(ui): redesign user dashboard

Complete overhaul of the user dashboard with improved
navigation and responsive design.

Co-authored-by: Jane Smith <jane@example.com>
```

### Multiple Co-authors
```bash
fix(database): optimize complex reporting queries

Refactor expensive queries and add proper indexing
to improve report generation performance by 75%.

Co-authored-by: John Doe <john@example.com>
Co-authored-by: Jane Smith <jane@example.com>
```

### Full Format with Co-authors
```bash
feat(security)!: implement two-factor authentication

Add TOTP-based 2FA for enhanced account security.
Users will be prompted to set up 2FA on next login.

BREAKING CHANGE: Authentication flow now requires
2FA verification for all admin users.

Co-authored-by: Security Team <security@example.com>
Closes #789
```

---

## 🔄 Common Workflows

### Feature Branch Workflow
```bash
# Start feature
feat(user-profile): add avatar upload functionality

# Incremental commits
feat(user-profile): implement image validation
feat(user-profile): add image resizing and optimization
test(user-profile): add avatar upload test suite
docs(user-profile): update API documentation for avatars

# Final commit
feat(user-profile): complete avatar upload implementation

Merge branch 'feature/user-avatars' into main
```

### Hotfix Workflow
```bash
# Emergency fix
hotfix: resolve critical payment gateway timeout

Production payment gateway experiencing timeouts due to
increased traffic. Implement circuit breaker pattern
and increase timeout values.

Fixes #URGENT-001

# Follow-up improvement
perf(payment): optimize gateway connection pooling

Reduce connection overhead and improve reliability
for high-traffic scenarios.

Related to hotfix commit abc123
```

### Bug Fix with Investigation
```bash
fix(email): resolve template rendering error

Email templates were failing to render due to missing
variable sanitization. Investigation revealed that
user input wasn't being properly escaped.

Root cause: Missing HTML encoding in template engine
Solution: Add XSS protection and input validation

Steps to reproduce:
1. Create email with special characters in subject
2. Send email through template system
3. Observe rendering failure

Fixes #567
Tested-by: QA Team <qa@example.com>
```

---

## ❌ Anti-patterns

### ❌ What NOT to Do

```bash
# Too vague
fix: bug fix

# Past tense
feat: added new feature

# Too long subject line (over 50 chars)
feat(authentication): implement comprehensive OAuth2 integration with Google, Facebook, and GitHub providers

# No type
update user validation

# Multiple changes in one commit
feat: add user registration and fix payment bug and update docs

# Unclear scope
fix(stuff): various fixes

# Personal/emotional language
fix: finally got this stupid bug working!!!

# Non-descriptive
misc changes
```

### ✅ Better Alternatives

```bash
# Clear and specific
fix(auth): resolve token expiration edge case

# Imperative mood
feat(auth): add OAuth2 integration

# Appropriate length
feat(auth): implement OAuth2 integration

Add support for Google, GitHub, and Facebook
authentication providers with token refresh.

# Proper type
feat: add user input validation

# Single responsibility
feat: add user registration system

fix(payment): resolve transaction timeout error

docs: update API authentication guide

# Clear scope
fix(payment): resolve gateway timeout issue

# Professional tone
fix(validation): resolve email format validation bug
```

---

## 📏 Commit Message Guidelines

### Subject Line Rules
- **Length**: Maximum 50 characters (GitHub truncates at 72)
- **Mood**: Use imperative mood ("Add", not "Added" or "Adds")
- **Case**: Start with lowercase after type (conventional style)
- **Punctuation**: No period at the end
- **Content**: Describe what the commit does, not what you did

### Body Guidelines
- **Width**: Wrap at 72 characters for better readability
- **Separation**: Blank line between subject and body
- **Content**: Explain *what* and *why*, not *how*
- **Lists**: Use bullet points or numbered lists for multiple items
- **Paragraphs**: Separate concerns with blank lines

### Footer Guidelines
- **References**: Link to issues, PRs, or external resources
- **Breaking Changes**: Use `BREAKING CHANGE:` keyword
- **Co-authors**: Use `Co-authored-by:` for collaboration
- **Other**: `Signed-off-by:`, `Reviewed-by:`, `Tested-by:`

### Length Examples

```bash
# Perfect length (49 chars)
feat(api): add user authentication middleware

# Too long (67 chars) - will be truncated
feat(api): add comprehensive user authentication middleware system

# Better alternative - move details to body
feat(api): add user authentication middleware

Implement comprehensive authentication system with
JWT token validation, role-based access control,
and session management.
```

---

## 🪝 Git Hooks

### Pre-commit Hook for Message Validation

Create `.git/hooks/commit-msg`:

```bash
#!/bin/sh
# Validate commit message format

commit_regex='^(feat|fix|docs|style|refactor|perf|test|build|ci|chore|security|hotfix|wip|revert)(\(.+\))?(!)?: .{1,50}'

if ! grep -qE "$commit_regex" "$1"; then
    echo "❌ Invalid commit message format!"
    echo "Use: type(scope): description"
    echo "Types: feat, fix, docs, style, refactor, perf, test, build, ci, chore, security, hotfix, wip, revert"
    echo "Max 50 characters for subject line"
    exit 1
fi

# Check subject line length
subject=$(head -1 "$1")
if [ ${#subject} -gt 50 ]; then
    echo "❌ Subject line too long (${#subject} chars, max 50)"
    exit 1
fi

echo "✅ Commit message format is valid"
```

### Make Hook Executable
```bash
chmod +x .git/hooks/commit-msg
```

### Pre-commit Hook for Code Quality
```bash
#!/bin/sh
# Pre-commit checks

echo "🔍 Running pre-commit checks..."

# Check for TODO/FIXME in staged files
if git diff --cached --name-only | xargs grep -l "TODO\|FIXME" 2>/dev/null; then
    echo "⚠️  Found TODO/FIXME in staged files"
    echo "Consider addressing them or use 'wip:' commit type"
fi

# Prevent commits to main branch
branch=$(git rev-parse --abbrev-ref HEAD)
if [ "$branch" = "main" ] || [ "$branch" = "master" ]; then
    echo "❌ Direct commits to $branch are not allowed"
    echo "Create a feature branch instead"
    exit 1
fi

echo "✅ Pre-commit checks passed"
```

### Global Git Hooks Setup
```bash
# Set global hooks directory
git config --global core.hooksPath ~/.githooks

# Create global hooks directory
mkdir -p ~/.githooks

# Copy your hooks to global directory
cp .git/hooks/commit-msg ~/.githooks/
chmod +x ~/.githooks/commit-msg
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
| 🔒     | `security` | 🔒 security: fix XSS vulnerability               |
| 🚑     | `hotfix` | 🚑 hotfix: resolve critical payment error          |
| 🚧     | `wip`   | 🚧 wip: experimenting with new architecture          |
| ⚡     | `perf`  | ⚡ perf: optimize database queries                   |
| 🔀     | n/a     | 🔀 merge branch 'feature/new-api'                   |

---

## 🔗 Reference Links

### Official Specifications
- [Conventional Commits Specification](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [Git Documentation - Commit Messages](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#_commit_guidelines)

### Style Guides
- [Angular Commit Message Guidelines](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#commit)
- [Conventional Changelog](https://github.com/conventional-changelog/conventional-changelog)
- [GitMoji - Emoji Guide](https://gitmoji.dev/)

### Tools and Validation
- [Commitizen](https://github.com/commitizen/cz-cli) - Interactive commit message tool
- [Commitlint](https://github.com/conventional-changelog/commitlint) - Lint commit messages
- [Husky](https://github.com/typicode/husky) - Git hooks made easy
- [Conventional Commits VSCode Extension](https://marketplace.visualstudio.com/items?itemName=vivaxy.vscode-conventional-commits)

### GitHub Integration
- [Automatically closing issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)
- [GitHub Co-authored commits](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors)
- [Squash and merge strategies](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges)

### Best Practices Articles
- [How to Write Better Git Commit Messages](https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/)
- [The Art of the Commit](https://alistapart.com/article/the-art-of-the-commit/)
- [5 Useful Tips For A Better Commit Message](https://thoughtbot.com/blog/5-useful-tips-for-a-better-commit-message)

---


## 💡 Quick Tips Summary

- **Subject line**: 50 characters max, imperative mood, no period
- **Body**: 72 characters per line, explain *what* and *why*
- **Use types**: feat, fix, docs, style, refactor, perf, test, build, ci, chore
- **Breaking changes**: Use `!` in subject and `BREAKING CHANGE:` in footer
- **Be specific**: "fix(auth): resolve token refresh bug" vs "fix: bug"
- **One concern per commit**: Easier to review, revert, and understand
- **Link issues**: Use "Closes #123", "Fixes #456", "Refs #789"

---
