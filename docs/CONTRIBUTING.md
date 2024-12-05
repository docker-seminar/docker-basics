# How to contribute to docker-basic

Thank you for your interest in contributing to the `docker-basic` repository!
This repository is designed to help individuals learn and grow in their understanding of Docker.
Below are the guidelines for contributing to the main branch, which serves as a template for all users.

---

# Notes on Personal Learning Branches

- **Learn Freely**: Feel free to experiment, practice, and commit your Docker learning journey in your own branch.
- **Create Pull Requests for Personal Branches**: You must create pull requests for your personal learning branches.
  This allows others to review your progress, provide feedback, and engage in constructive discussions to help enhance
  your learning experience.
- **No PRs to the Main Branch**: Do not submit pull requests from your personal branches to the main branch.
  Contributions to the main branch follow separate guidelines (see below).

---

# Contributing to the Main Branch

The main branch serves as a polished template for all users.
Contributions should focus on improving or expanding the content for general use.

## What Can You Contribute?

- **Enhancements**: Improve clarity, examples, or documentation in the main branch.
- **New Features**: Add GitHub workflows to check spelling, continuous integration, issue templates and so on.

## Contribution Process

1. **Create an Issue**:
   Before contributing, create an issue to discuss the proposed change. This ensures alignment with the repository's
   goals and allows others to provide input.

2. **Create a Branch**:
   Check out a new branch directly in the repository to work on your contribution. Use issue number as branch name:
   ```bash
   git checkout -b feat/ISSUE_NUMBER
   ```
   Replace ISSUE_NUMBER with the actual number. For bug fixes, use `fix/` prefix, for infrastructures, use `infra/`
   prefix.

3. **Make Your Changes**:
   Implement your changes while ensuring they align with the repository's style and purpose. Keep your changes focused
   and relevant.

4. **Test Your Changes**:
   Thoroughly test your updates to ensure they work as intended and do not introduce new issues. If applicable, write
   additional tests to cover your changes.

5. **Commit Your Changes**:
   Write a clear and descriptive commit message summarizing the purpose of your changes:
    ```bash
    git commit -m "infra(integration): Add GitHub Issue template"
    ```

6. **Push Your Branch**:
   Push your branch to the repository:
    ```bash
   git push origin feat/ISSUE_NUMBER
    ```

7. **Open a Pull Request**:
    - Select main branch as the base branch.
    - Provide a detailed description of your changes, referencing the issue you created earlier.

8. **Participate in the Review Process**:
    - Be responsive to feedback from reviewers.
    - Make updates to your pull requests as needed.
    - Engage in constructive discussions to finalize your contribution.
