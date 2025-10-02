# Code-Review MVP

✨ Lightweight Automated Code Review Workflow

This project is a minimal, working code review assistant. It automatically fixes small issues and enforces clean code in pull requests so reviewers can focus on logic, not formatting.

⸻

## 🚀 Features

• Auto-fix on save/commit with ESLint + Prettier + Husky.  
• PR checks via GitHub Actions (runs lint + format check).  
• Fast setup — add one workflow file and you’re done.  
• Keeps repos clean — reviewers focus on logic, not style.

⸻

## 📦 Quick Start (Local)

```bash
# clone your repo
git clone https://github.com/your-username/code-review-mvp.git
cd code-review-mvp

# install dependencies
npm install

# enable husky (for pre-commit hooks)
npx husky init
```

• Save a file → Prettier formats automatically.  
• Commit → Husky + lint-staged auto-fix small issues.

⸻

## 🔄 GitHub Action (PR Checks)

This workflow runs on every Pull Request:

```yaml
name: PR Quality
on: [pull_request]
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci || npm i
      - run: npm run lint
      - run: npm run format -- --check
```

⸻

## 🧑‍💻 Example

**Failing PR (before):**  
![PR failing](docs/pr-fail.png)

**Passing PR (after):**  
![PR passing](docs/pr-pass.png)

_Local commits (Husky):_ When committing locally, Husky + lint-staged run Prettier/ESLint:  
• Small issues (spacing, semicolons) → auto-fixed.  
• Serious issues (like undefined variables) → commit blocked.

⸻

## 🎯 Why This Matters

Code reviews often waste time on small style issues. This workflow:  
• Reduces noise (no more “add a semicolon” comments).  
• Saves time for both authors and reviewers.  
• Keeps code clean and consistent across projects.

⸻

## 📌 Roadmap

- [x] Add ESLint + Prettier setup
- [x] Add Husky + lint-staged pre-commit hooks
- [x] Add GitHub Action for PR checks
- [ ] Add reusable GitHub Action (uses: code-review-mvp@v1)
- [ ] Add Danger rule (warn if PR too big or missing description)
- [ ] Add optional TypeScript support (tsc --noEmit)

⸻

## 📄 License

MIT License © 2025 Luba Kaper
