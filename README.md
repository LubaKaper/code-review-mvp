Code-Review MVP

✨ Lightweight Automated Code Review Workflow

This project is a minimal, working code review assistant. It automatically fixes small issues and enforces clean code in pull requests so reviewers can focus on logic, not formatting.

⸻

🚀 Features
• Auto-fix on save/commit with ESLint + Prettier + Husky.
• PR checks via GitHub Actions (runs lint + format check).
• Fast setup — add one workflow file and you’re done.
• Project-only or reusable — works in your repo or as a reusable GitHub Action.

⸻

📦 Quick Start (Local)

<pre>
```bash
# clone your repo
git clone https://github.com/your-username/code-review-mvp.git
cd code-review-mvp

# install dependencies
npm install

# enable husky (for pre-commit hooks)
npx husky init
```
</pre>

    •	Save a file → Prettier formats automatically.
    •	Commit → Husky + lint-staged auto-fix small issues.

⸻

🔄 GitHub Action (PR Checks)

Add this workflow in .github/workflows/pr-quality.yml to run checks on pull requests:

<pre>
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
</pre>

🧑‍💻 Example

PR with messy code → ❌ fails checks.
After auto-fix + push → ✅ passes, ready to merge.

(Add screenshots or a short GIF here once you test it)

⸻

🎯 Why This Matters

Code reviews often waste time on small style issues. This workflow:
• Reduces noise (no more “add a semicolon” comments).
• Saves time for both authors and reviewers.
• Keeps code clean and consistent across projects.

⸻

📌 Roadmap
• Reusable GitHub Action (uses: your-username/code-review-mvp@v1)
• Simple Danger rule (warn if PR too big or missing description)
• Optional TypeScript support (tsc --noEmit)

⸻

📄 License

MIT License © 2025 Luba Kaper
