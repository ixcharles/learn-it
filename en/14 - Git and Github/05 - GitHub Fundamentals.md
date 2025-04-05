
# GitHub Fundamentals

This course introduces essential GitHub functionalities that enhance collaboration, version control, and automation, enabling developers to work more efficiently in team environments.

## Table of Contents

1. [Introduction to GitHub](#introduction-to-github)
2. [Creating and Managing Repositories on GitHub](#creating-and-managing-repositories-on-github)
3. [Cloning GitHub Repositories](#cloning-github-repositories)
4. [Forking Repositories and Pull Requests](#forking-repositories-and-pull-requests)
5. [Issues and Issue Tracking on GitHub](#issues-and-issue-tracking-on-github)
6. [GitHub Projects and Milestones](#github-projects-and-milestones)
7. [Collaborating with GitHub Teams](#collaborating-with-github-teams)
8. [GitHub Actions and CI/CD Basics](#github-actions-and-cicd-basics)

---

## Introduction to GitHub

GitHub is a platform for hosting and collaborating on Git repositories. It allows developers to store code, track issues, and collaborate through pull requests.

**Example:**
Create a free account on [GitHub](https://github.com) to start collaborating on open-source projects.

---

## Creating and Managing Repositories on GitHub

To create a repository on GitHub:
1. Go to your GitHub dashboard.
2. Click the "New" button to create a new repository.
3. Name the repository, add a description, and initialize with a README.

You can manage a repository's settings, such as visibility (public/private), collaborators, and branch protection rules.

**Example:**
1. Create a new repository at [https://github.com/new](https://github.com/new).
2. Clone the repository to your local machine and push changes.

---

## Cloning GitHub Repositories

To clone a GitHub repository to your local machine:
1. Navigate to the repository on GitHub.
2. Copy the repository URL.
3. Run `git clone <repo_url>`.

**Example:**
```bash
git clone https://github.com/username/repo.git
```

---

## Forking Repositories and Pull Requests

Forking allows you to create a personal copy of someone else's repository to experiment with changes without affecting the original.

1. Click "Fork" on the original repository page.
2. After forking, clone the repository to your local machine.
3. Create a new branch, make changes, and push to your fork.
4. Open a pull request to propose merging your changes into the original repository.

**Example:**
```bash
git clone https://github.com/your-username/repo.git
git checkout -b feature-branch
git push origin feature-branch
```
Then, create a pull request on GitHub.

---

## Issues and Issue Tracking on GitHub

GitHub Issues allow you to track bugs, tasks, and enhancements. You can create, assign, label, and close issues within a repository.

- **Create an Issue**: Click on "Issues" in the repository, then "New Issue".
- **Assign Issues**: Assign issues to team members for resolution.
- **Label Issues**: Organize issues with labels like "bug", "enhancement", or "help wanted".

**Example:**
Create an issue to report a bug:
- Title: "App crashes on login"
- Description: "Describe the steps to reproduce the issue."

---

## GitHub Projects and Milestones

- **Projects**: GitHub Projects allow you to organize tasks, bugs, and features in a Kanban-style board.
- **Milestones**: Milestones are used to group issues and pull requests that are related to a specific release or goal.

**Example:**
1. Create a project board to track tasks in the repository.
2. Use milestones to track the progress of a feature or release.

---

## Collaborating with GitHub Teams

GitHub Teams provide a way to organize members into groups with specific permissions for repositories.

- **Create a Team**: Go to the repository or organization, and click on "Teams".
- **Assign Permissions**: Set repository access levels for each team (e.g., read, write, admin).
- **Collaborate**: Team members can review pull requests, create issues, and contribute to the repository.

**Example:**
- Create a "frontend" team for members working on the frontend code with write access to the repository.

---

## GitHub Actions and CI/CD Basics

GitHub Actions allows you to automate workflows like continuous integration (CI) and continuous deployment (CD). 

- **Create a Workflow**: Define a `.github/workflows` YAML file to specify triggers, such as on push or pull request.
- **Build and Test**: Automate testing and building processes to run whenever code is pushed to a repository.

**Example:**
A simple CI workflow for running tests:
```yaml
name: Node.js CI

on: [push, pull_request]

jobs:
  build:
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

## Conclusion

### Key Takeaways:
1. GitHub allows for collaboration on Git repositories, with features like pull requests, forking, and issues tracking.
2. You can create and manage repositories, assign issues, and track progress with Projects and Milestones.
3. Forking enables contributing to open-source projects without affecting the original repository.
4. GitHub Teams facilitate collaboration with different permission levels on repositories.
5. GitHub Actions helps automate CI/CD workflows directly within GitHub.

### Practical Exercise:
1. Create a repository on GitHub, clone it to your local machine, and push changes.
2. Fork a repository, make changes, and submit a pull request.
3. Create an issue for a bug, track it using a project, and automate tests using GitHub Actions.
