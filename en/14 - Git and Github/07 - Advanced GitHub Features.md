
# Advanced GitHub Features

This course covers advanced features of GitHub that enhance project management, automation, security, and integrations, enabling developers to take full advantage of GitHub's ecosystem.

## Table of Contents

1. [GitHub Pages and Hosting Projects](#github-pages-and-hosting-projects)
2. [GitHub Actions for CI/CD Pipelines](#github-actions-for-cicd-pipelines)
3. [GitHub API and Integrations](#github-api-and-integrations)
4. [Managing GitHub Workflows with Actions](#managing-github-workflows-with-actions)
5. [Securing GitHub Repositories (Branch Protection, 2FA)](#securing-github-repositories-branch-protection-2fa)
6. [GitHub Packages and Dependency Management](#github-packages-and-dependency-management)

---

## GitHub Pages and Hosting Projects

GitHub Pages allows you to host static websites directly from a GitHub repository.

- **Creating GitHub Pages**: Create a branch named `gh-pages` or use the `main` branch, and push your static files.
- **Custom Domain**: You can link a custom domain by configuring the `CNAME` file.

**Example:**
1. Create a repository (e.g., `username.github.io`).
2. Push your HTML, CSS, and JavaScript files.
3. Visit `https://username.github.io` to see your site live.

---

## GitHub Actions for CI/CD Pipelines

GitHub Actions automates workflows like Continuous Integration (CI) and Continuous Deployment (CD).

- **Creating Actions**: Define actions in the `.github/workflows` directory using YAML configuration.
- **Running Tests and Deploying**: Automatically run tests and deploy your app after every commit.

**Example:**
```yaml
name: CI Pipeline

on:
  push:
    branches:
      - main

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

## GitHub API and Integrations

GitHub’s API allows you to automate interactions with repositories, issues, pull requests, and more.

- **Creating Personal Access Tokens**: Use tokens to authenticate API requests securely.
- **Integrations**: Integrate GitHub with third-party services like Slack, JIRA, and Jenkins.

**Example**: 
1. Create a token at [GitHub’s token page](https://github.com/settings/tokens).
2. Use the API to list all repositories:
```bash
curl -H "Authorization: token YOUR_PERSONAL_ACCESS_TOKEN" https://api.github.com/user/repos
```

---

## Managing GitHub Workflows with Actions

GitHub workflows automate tasks based on events like pushes, pull requests, or issues. They consist of jobs and steps executed sequentially.

- **Workflow Triggers**: Use triggers like `push`, `pull_request`, and `schedule` to start workflows.
- **Jobs and Steps**: Jobs can run on specific environments, and steps execute commands in sequence.

**Example**:
```yaml
name: Deploy Application

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Deploy to server
        run: ./deploy.sh
```

---

## Securing GitHub Repositories (Branch Protection, 2FA)

Security features ensure code integrity and protect your GitHub repositories.

- **Branch Protection**: Enforce rules to prevent direct pushes, require reviews, or require status checks for certain branches.
- **Two-Factor Authentication (2FA)**: Add an extra layer of security by requiring 2FA for access to repositories.

**Example**:
1. Enable 2FA in GitHub’s settings under **Security**.
2. Set branch protection under **Settings > Branches** to require pull requests before merging.

---

## GitHub Packages and Dependency Management

GitHub Packages is a package registry that allows you to publish, share, and manage dependencies directly within GitHub repositories.

- **Publishing Packages**: Use GitHub Packages to publish Docker images, npm packages, or other artifacts.
- **Dependency Management**: Manage and install dependencies using GitHub's package registry in projects like Node.js or Python.

**Example (npm)**:
1. Add a package to the registry:
```bash
npm publish --access public
```
2. Install a package:
```bash
npm install @username/package-name
```

---

## Conclusion

### Key Takeaways:
1. **GitHub Pages** allows for hosting static websites directly from repositories.
2. **GitHub Actions** streamlines CI/CD processes by automating builds, tests, and deployments.
3. **GitHub API** enables programmatic access to repository data and integrates with other tools.
4. **Securing Repositories** is crucial for protecting code with branch protection and enforcing 2FA.
5. **GitHub Packages** facilitates the sharing and management of software packages and dependencies.

### Practical Exercise:
1. Set up a GitHub Pages site for a personal project.
2. Create a simple CI workflow using GitHub Actions to run tests whenever code is pushed.
3. Explore the GitHub API by authenticating with a personal access token and listing your repositories.
4. Enable branch protection on the `main` branch of your repository and require pull request reviews before merging.
5. Publish a package to GitHub Packages and integrate it into another project.
