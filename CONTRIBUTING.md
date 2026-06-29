# Contributing to CyberRangeCZ

Thank you for your interest in contributing to CyberRangeCZ — an open-source platform for building,
delivering, and managing advanced cybersecurity training environments. This document describes the
shared conventions that apply across **all repositories** in the
[cyberrangecz](https://github.com/cyberrangecz) organisation.

> **Repository-specific setup** (local build steps, test commands, language conventions) is covered in
> each repository's own `CONTRIBUTING.md` or `README.md`. Start here, then check there.

---

## Table of Contents

- [Contributing to CyberRangeCZ](#contributing-to-cyberrangecz)
  - [Table of Contents](#table-of-contents)
  - [Code of Conduct](#code-of-conduct)
  - [Where to Get Help](#where-to-get-help)
  - [Repository Map](#repository-map)
  - [How to Contribute](#how-to-contribute)
    - [Reporting Bugs](#reporting-bugs)
    - [Suggesting Enhancements](#suggesting-enhancements)
    - [Contributing Code](#contributing-code)
  - [Branch \& Commit Conventions](#branch--commit-conventions)
    - [Branch Naming](#branch-naming)
    - [Commit Messages](#commit-messages)
  - [Pull Request Process](#pull-request-process)
  - [Coding Standards](#coding-standards)
  - [Security Vulnerabilities](#security-vulnerabilities)
  - [License](#license)

---

## Code of Conduct

We are committed to a welcoming and respectful community. All contributors are expected to:

- Use inclusive and professional language.
- Respect differing viewpoints and experiences.
- Accept constructive criticism gracefully.
- Show empathy towards other community members.

Unacceptable behaviour may be reported to the maintainers via the
[CyberRangeCZ contact page](https://www.cyberrange.cz/contact/). Reports are treated confidentially.

---

## Where to Get Help

| Need | Where to go |
|---|---|
| New features suggestions, Platform usage & deployment questions | [GitHub Discussions](https://github.com/orgs/cyberrangecz/discussions) |
| Bug reports & feature requests | Issues in the relevant repository |
| Cross-repo / platform-wide issues | [cyberrangecz/issues](https://github.com/cyberrangecz/issues) |
| Full platform documentation | [docs.platform.cyberrange.cz](https://docs.platform.cyberrange.cz) |
| Commercial support & custom integration | [cyberrange.cz/contact](https://www.cyberrange.cz/contact/) |

---

## Repository Map

CyberRangeCZ is a microservices platform. The main areas are:

| Area | Repositories |
|---|---|
| **Infrastructure / Deployment** | `devops-helm`, `devops-tf-deployment`, `tf-module-helm`, `tf-module-openstack-*` |
| **Sandbox** | `backend-sandbox-service`, `backend-openstack-lib` |
| **Training** | `backend-training`, `backend-adaptive-training`, `backend-adaptive-smart-assistant`, `backend-training-feedback`, `backend-answers-storage` |
| **Frontend** |  `frontend-platform` |
| **Provisioning / Clients** | `go-client`, `ansible-stage-one`, `ansible-role-*` |
| **Documentation** | `docs` |

---

## How to Contribute

### Reporting Bugs

1. **Search existing issues** in the relevant repository before opening a new one.
2. If none exists, open an issue and include:
   - A clear, descriptive title.
   - Steps to reproduce the problem.
   - Expected vs. actual behaviour.
   - Environment details (platform version, cloud backend — OpenStack or AWS, Kubernetes version).
   - Relevant logs or screenshots.

Issues labelled **`good first issue`** are a great starting point for new contributors.

### Suggesting Enhancements

Open an issue with the label `enhancement` and describe:

- The problem you are trying to solve (not just the solution).
- Your proposed solution and any alternatives you considered.
- Whether this is platform-wide or specific to one service.

### Contributing Code

1. **Open or find an issue** that describes the change you want to make. If none exists, create one and wait for maintainer acknowledgement before starting work.
2. **Fork** the repository you want to contribute to.
3. **Clone** your fork locally.
4. Follow the repo-specific setup instructions in its `README.md`.
5. Create a feature branch (see [Branch Conventions](#branch--commit-conventions)).
6. Make your changes, add tests, update docs.
7. Push and open a Pull Request against the `master` (or `develop`) branch of the upstream repo, linking the issue in the description.

---

## Branch & Commit Conventions

### Branch Naming

```
<type>/<short-description>
```

| Type | When to use |
|---|---|
| `feature/` | New functionality |
| `fix/` | Bug fixes |
| `chore/` | Build, CI, dependency updates |
| `docs/` | Documentation only |
| `refactor/` | Code restructuring without behaviour change |

Examples: `feature/adaptive-hint-scoring`, `fix/sandbox-pool-timeout`, `docs/helm-chart-values`

### Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>(<optional scope>): <short summary>

[optional body]

[optional footer: closes #<issue-number>]
```

Examples:
```
feat(sandbox): add support for AWS multi-region pools
fix(training): prevent null pointer on empty hint list
docs: update Helm chart README with new auth config
```

- Use the **imperative mood** in the summary ("add support", not "added support").
- Keep the summary line under 72 characters.
- Reference issues in the footer: `Closes #42`.

---

## Pull Request Process

> **Before opening a PR, you must create an issue.** Every pull request must be backed by an issue
> with a detailed description of the problem or change. PRs without a linked issue will not be
> reviewed and may be closed. This applies to all contribution types — features, bug fixes, docs,
> and refactors alike.

1. **Open an issue first** (see [Reporting Bugs](#reporting-bugs) or
   [Suggesting Enhancements](#suggesting-enhancements)) and wait for maintainer acknowledgement
   before investing significant effort in an implementation.
2. **Link the issue** your PR addresses in the description (`Closes #<number>`).
2. **Keep PRs focused** — one logical change per PR makes review faster.
3. **Fill in the PR template** if one exists in the repository.
4. **Ensure CI passes** — all GitHub Actions checks must be green before review.
5. **Request a review** from at least one maintainer (use the *Reviewers* panel).
6. **Address review feedback** promptly; mark conversations resolved once actioned.
7. A maintainer will merge the PR once it is approved and CI is green.
   - Preference is **squash merge** for feature branches, **merge commit** for release branches.

---

## Coding Standards

The platform is polyglot — specific linting rules live in each repo. The following apply everywhere:

- **No secrets in code.** Never commit credentials, tokens, API keys, or passwords. Use environment variables or Kubernetes secrets.
- **All public APIs must be documented.** REST endpoints, public functions, and Helm chart values require docstrings / comments.
- **Write tests for new behaviour.** Bugfixes should include a regression test.
- **Pre-commit hooks.** If the repository ships a `.pre-commit-config.yaml`, install and run pre-commit before pushing:
  ```bash
  pip install pre-commit
  pre-commit install
  ```
- **Infrastructure as code.** Terraform/OpenTofu and Helm changes must be validated (`terraform validate`, `helm lint`) before submitting.

---

## Security Vulnerabilities

**Do not open a public GitHub issue for security vulnerabilities.**

Please report security issues privately via the
[CyberRangeCZ contact page](https://www.cyberrange.cz/contact/). Maintainers will acknowledge
receipt within 5 business days and work with you on a coordinated disclosure.

---

## License

All CyberRangeCZ repositories are released under the **[MIT License](https://opensource.org/licenses/MIT)**.
By contributing, you agree that your contributions will be licensed under the same terms.

---

*CyberRangeCZ builds on the innovation started by KYPO CRP at Masaryk University and is now
stewarded by [CyberSecurity Hub, z.s.](https://www.cyberrange.cz/)*
