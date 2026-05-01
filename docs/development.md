# Development Guideline

To maintain code quality, ensure consistency, and enable smooth collaboration across the team, it is essential to follow a standardized development workflow. This document outlines best practices for contributing to the project. By adhering to these guidelines, we can reduce bugs, improve readability, and speed up reviews and integration.

---

## 1. Branch Management

- All development code must be submitted to the `dev` branch.
- Do **not** push code directly to the `main` branch.
- All new features, bug fixes, and experiments should be done in the `dev` branch or a feature branch based on `dev`.
- Rather than creating duplicate code via copy-paste, modify the existing code directly in the `dev` branch. Do not worry about breaking things. Git will track all changes, and GitHub provides an easy-to-read visual comparison for reviewing edits.

---

## 2. Code Style and Documentation

- **Write modular, reusable functions** instead of duplicating code through copy-paste.
- Use **NumPy-style docstrings** for all functions and modules.
- Use **Python type hints** to improve clarity and robustness.
- Format your code using [`black`](https://github.com/psf/black) to enforce consistency.
- Run [`flake8`](https://flake8.pycqa.org/) to check for style issues and potential bugs.

---

## 3. Testing

- Each module in the source code should have a corresponding test file placed in the `tests/` directory.
- Use [`pytest`](https://docs.pytest.org/) to implement and run unit tests.
- Tests should cover core logic and include edge cases.
- Make sure your code **passes all tests** before pushing to GitHub.

---

## 4. Commit Best Practices

- Update your code regularly in small, manageable chunks.
- Avoid large, monolithic commits because they are harder to review and debug.
- (Optional) Follow the [Conventional Commits](https://www.conventionalcommits.org/) style for consistency.

---

## 5. Pull Requests

- Open a **Pull Request (PR)** when contributing to the `main` branch.
- A reviewer will be notified, review your code, and provide feedback.
- Revise your code based on the feedback before merging into `main`.
- **Keep each PR focused on one clear topic**. Avoid bundling unrelated changes into a single PR.

---

## 6. Collaboration Tips

- Regularly pull the latest changes from the `dev` branch to avoid conflicts.
- Communicate before making major changes to ensure team alignment.
- Don’t hesitate to ask questions or reach out by opening an issue on GitHub.

---

## 7. System-Level Thinking

- Treat the project as a **coherent system**, not a collection of independent components.
- **Align with existing abstractions and structure** — avoid introducing parallel or ad hoc designs.
- Before implementing, understand the **implicit contracts** in the codebase: interfaces, data semantics, structural assumptions, and downstream dependencies.
- Distinguish between **local decisions** (implementation details) and **system-wide decisions** (interfaces, structure, semantics). The latter require team communication.
- **Communicate early** when your changes affect interfaces, outputs, thresholds, or other people's work. Avoid silent behavioral changes.
- If the intended integration is unclear, **ask before implementing**.

---

## 8. Working with AI Coding Agents

- AI coding agents (e.g., Claude Code, Codex, Cursor) are **productivity tools, not decision-makers**. The developer is responsible for all code that gets committed.
- **Always review AI-generated code** before committing. It must meet the same standards outlined in Sections 1–7.
- AI agents tend to **over-engineer**. Watch for unnecessary abstractions, excessive indirection, and overly complex solutions to simple problems. Prefer simple, readable code.
- Use AI agents for **well-scoped tasks**: writing boilerplate, generating tests, drafting docstrings, exploring implementation options. Avoid delegating system-wide design decisions to them.
- When using AI agents in collaborative workflows, **note it in your PR description** so reviewers can apply appropriate scrutiny.
- **Do not paste sensitive data** (credentials, API keys, internal datasets) into AI tools that are not approved for use with confidential information.

---

## References

- Beck K, et al. [Manifesto for agile software development](https://agilemanifesto.org/).
- Brooks F. [*The Mythical Man-Month: Essays on Software Engineering*](https://web.eecs.umich.edu/~weimerw/2018-481/readings/mythical-man-month.pdf). Addison-Wesley.
- Browning B. [An introduction to genotype imputation](https://www.youtube.com/watch?v=-oUvXXg6tl8). Computational Genomics Summer Institute 2016 at the Institute for Pure and Applied Mathematics.
- Google. [Google Style Guides](https://google.github.io/styleguide/).
- Lopopolo R. [Harness engineering: leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/). OpenAI.
- Peters T. [The Zen of Python](https://peps.python.org/pep-0020/). Python Software Foundation.
- Shannon C. [Creative Thinking](https://www.cs.bilkent.edu.tr/~canf/CS533/claude-shannon-creative-thinking.pdf). Bell Lab.
- Wilson G, et al. [Best practices for scientific computing](https://doi.org/10.1371/journal.pbio.1001745). *PLoS Biology* **12**: e1001745.
