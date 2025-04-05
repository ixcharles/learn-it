
# Git and GitHub in Team Environments

This course explores best practices and strategies for using Git and GitHub effectively in collaborative team settings, covering branching strategies, permissions, CI/CD workflows, and more.

## Table of Contents

1. [Branching Strategies for Teams](#branching-strategies-for-teams)
2. [Managing Permissions and Access Control](#managing-permissions-and-access-control)
3. [Continuous Integration and Continuous Deployment with GitHub Actions](#continuous-integration-and-continuous-deployment-with-github-actions)
4. [Using Git Hooks for Automation](#using-git-hooks-for-automation)
5. [Collaborating on Large Projects with Git](#collaborating-on-large-projects-with-git)
6. [Workflow Best Practices for Distributed Teams](#workflow-best-practices-for-distributed-teams)

---

## Branching Strategies for Teams

Branching strategies help teams maintain clean, organized repositories and workflows.

### Common Branching Strategies:
- **Git Flow**: Use dedicated branches for `feature`, `develop`, `release`, and `hotfix`.
- **GitHub Flow**: Simplified model using a `main` branch with short-lived feature branches.
- **Feature Branching**: Create a new branch for each feature or bug fix.

**Example:**
```bash
# Using GitHub Flow
git checkout -b feature-new-design
git push origin feature-new-design
```

---

## Managing Permissions and Access Control

GitHub allows teams to control access to repositories using various permission levels.

### Permission Levels:
- **Read**: View repository contents, clone the repository.
- **Write**: Make changes to the repository, push to branches.
- **Admin**: Full control over repository settings, including adding/removing collaborators.

### Controlling Access:
- Use **Teams** and **Organizations** to set permissions for groups.
- Enable **Branch Protection** rules to control who can push or merge into important branches.

**Example**:
- Assign **Write** permission to the development team and **Admin** to the repository owner.

---

## Continuous Integration and Continuous Deployment with GitHub Actions

GitHub Actions automates workflows like Continuous Integration (CI) and Continuous Deployment (CD).

### CI/CD with GitHub Actions:
- **Continuous Integration**: Run tests and linting on every push or pull request.
- **Continuous Deployment**: Automatically deploy applications to staging or production after successful tests.

**Example (CI pipeline for Node.js)**:
```yaml
name: CI Pipeline

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - run: npm install
      - run: npm test
```

---

## Using Git Hooks for Automation

Git hooks are scripts that run automatically at certain points during the Git lifecycle (e.g., before committing, before pushing).

### Common Hooks:
- **pre-commit**: Run checks before committing code (e.g., linting or tests).
- **post-commit**: Trigger actions after a commit is made (e.g., notification or deploy).
- **pre-push**: Run tests or checks before pushing to a remote repository.

**Example (pre-commit hook to run tests)**:
```bash
#!/bin/sh
npm run lint && npm test
```
Place the script in `.git/hooks/pre-commit`.

---

## Collaborating on Large Projects with Git

Large projects require careful management of branches, code reviews, and communication.

### Tips for Collaboration:
- **Keep Pull Requests Small**: Break down large features into small, manageable pull requests.
- **Use Labels and Milestones**: Track tasks and bugs, and prioritize with milestones.
- **Regularly Sync Forks**: Sync your fork with the upstream repository to keep it up to date.

**Example**:
- Fork the main repository and keep it up to date:
```bash
git remote add upstream https://github.com/original-owner/repo.git
git fetch upstream
git merge upstream/main
```

---

## Workflow Best Practices for Distributed Teams

Distributed teams often work across different time zones, requiring clear workflows and communication.

### Best Practices:
- **Standardize Branching**: Agree on a common branching model (e.g., GitFlow or GitHub Flow).
- **Frequent Pull Requests**: Encourage small, frequent pull requests to improve code quality and reduce merge conflicts.
- **Code Review Guidelines**: Define clear guidelines for reviewing code, including the types of feedback to provide (e.g., style, logic, documentation).
- **Automate Communication**: Use GitHub Actions to notify team members of key actions (e.g., when a PR is created or merged).

**Example**:
- Use Slack or email to notify the team whenever a new pull request is created or a deployment happens.

---

## Conclusion

### Key Takeaways:
1. **Branching Strategies** help teams work in parallel without interfering with each other's work (e.g., Git Flow, GitHub Flow).
2. **Permissions and Access Control** are crucial for managing team roles and ensuring the right people have the right level of access.
3. **CI/CD with GitHub Actions** streamlines development and deployment by automating testing and deployment pipelines.
4. **Git Hooks** automate common tasks like linting and testing before commits and pushes.
5. **Best Practices for Distributed Teams** focus on effective communication, regular pull requests, and standardized workflows.

### Practical Exercise:
1. Implement a branching strategy (e.g., GitHub Flow) for a new team project and push changes to a shared repository.
2. Set up a GitHub Action that runs tests on every push and notifies the team of the results.
3. Create a pre-commit hook that runs linting and tests before committing changes.
4. Collaborate on a large project by forking a repository, creating a pull request, and managing merge conflicts with teammates.
5. Define and document a set of code review guidelines for your team and implement them in your workflow.
