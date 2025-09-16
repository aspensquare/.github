# .github

This repository defines **organization-wide community health files** and GitHub defaults.  
These files are automatically inherited by all repositories in the org, unless a repo overrides them with its own versions.

## 📌 What’s in here?
- **Pull Request Templates** → Ensure all PRs follow a consistent structure
- **Issue Templates** → Standardized bug reports, feature requests, etc.
- **CONTRIBUTING.md** → Guidelines for how to contribute
- **CODEOWNERS** → Define code review responsibilities
- **Workflows** → Shared GitHub Actions (if enabled for this repo)

## 🔄 How it works
- If a repository **does not** have its own PR/issue templates, GitHub will fall back to the ones in this repo.
- Individual repos can still override any file by creating their own version.

## 🎯 Why this repo exists
- Consistency across all repos in the organization
- Saves contributors from guessing how to format PRs/issues
- Reduces review friction and improves maintainability

## 👩‍💻 Contributing
If you want to suggest changes to the default templates:
1. Open a PR in this `.github` repo
2. Tag relevant reviewers (see `CODEOWNERS` if defined)
3. Once merged, the changes apply org-wide

---

🚀 *These defaults help everyone move faster by keeping our repos consistent and contributor-friendly.*
