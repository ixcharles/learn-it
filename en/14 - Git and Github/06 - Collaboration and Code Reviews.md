
# Collaboration and Code Reviews

This course covers the core techniques and best practices for collaborating on GitHub, from forking repositories and managing pull requests to conducting code reviews and resolving conflicts.

## Table of Contents

1. [Forking, Pull Requests, and Merging on GitHub](#forking-pull-requests-and-merging-on-github)
2. [Reviewing Code and Providing Feedback](#reviewing-code-and-providing-feedback)
3. [Managing Merge Conflicts in Pull Requests](#managing-merge-conflicts-in-pull-requests)
4. [Managing Branch Permissions and Protected Branches](#managing-branch-permissions-and-protected-branches)
5. [Using Labels, Assignments, and Milestones for Issue Tracking](#using-labels-assignments-and-milestones-for-issue-tracking)
6. [Rebase vs. Merge in Pull Requests](#rebase-vs-merge-in-pull-requests)

---

## Forking, Pull Requests, and Merging on GitHub

### Forking
Forking creates a personal copy of a repository, allowing you to experiment or make changes without affecting the original.

- To fork, click the **Fork** button in the top-right of the GitHub repository.

### Pull Requests
Once changes are ready, open a pull request (PR) to merge your branch into the original repository.

1. **Create a Pull Request**: After pushing changes to a branch, click "New Pull Request" on GitHub.
2. **Review and Merge**: Collaborators review the PR. Once approved, it can be merged into the main repository.

**Example:**
```bash
git clone https://github.com/your-username/repo.git
git checkout -b feature-branch
git push origin feature-branch
```
Then create a pull request to merge `feature-branch` into `main`.

---

## Reviewing Code and Providing Feedback

Code reviews are an essential part of collaboration. Here’s how you can review and provide feedback:

- **Reviewing Changes**: View changes in the PR tab and check files modified.
- **Commenting**: Provide comments on specific lines using inline commenting.
- **Approving**: If the changes are satisfactory, approve the PR or request changes if improvements are needed.

**Example:**
- Comment: "Can you optimize this function?"
- Approve: "This looks good, I approve."

---

## Managing Merge Conflicts in Pull Requests

Merge conflicts occur when changes in two branches conflict and Git cannot automatically merge them. GitHub provides tools to help resolve conflicts.

1. **Identifying Conflicts**: GitHub will mark files with conflicts in the PR.
2. **Resolve Locally**: Pull the changes to your local repository, resolve conflicts, and push the resolution.

**Example:**
```bash
git fetch origin
git checkout feature-branch
git merge main
# Resolve conflicts manually in the conflicted files
git add <resolved-file>
git commit -m "Resolve merge conflicts"
git push origin feature-branch
```

---

## Managing Branch Permissions and Protected Branches

Protected branches are used to enforce rules on certain branches (e.g., `main`, `develop`) to ensure high code quality and prevent direct pushes.

- **Branch Protection Rules**: Define rules like requiring PR reviews, passing status checks, and restricting who can push to the branch.
- **Enforcing Rules**: Set rules under the repository's settings → **Branches** → **Add Rule**.

**Example**:
- You can require a successful CI check before merging or mandate that only certain users can push directly to `main`.

---

## Using Labels, Assignments, and Milestones for Issue Tracking

GitHub provides several tools to organize and prioritize work using **Labels**, **Assignments**, and **Milestones**.

### Labels
- **Labels** categorize issues (e.g., `bug`, `enhancement`, `help wanted`).

### Assignments
- Assign issues to collaborators for resolution.

### Milestones
- Use **Milestones** to track progress toward a particular goal or release.

**Example**:
- Label an issue `bug`, assign it to a team member, and add it to a milestone like `v1.0 Release`.

---

## Rebase vs. Merge in Pull Requests

- **Rebase**: Rewriting history to apply your changes on top of the target branch, keeping a cleaner linear history.
  - **Pros**: Creates a cleaner commit history.
  - **Cons**: Rewrites commit history, which can cause issues in shared branches.

- **Merge**: Combines the changes of two branches with a merge commit, preserving both histories.

**When to Use**:
- Use **Rebase** to maintain a clean commit history (ideal for feature branches).
- Use **Merge** to preserve the history of the branch, especially in shared or public branches.

**Example:**
- Rebase:
```bash
git fetch origin
git rebase origin/main
```
- Merge:
```bash
git merge feature-branch
```

---

## Conclusion

### Key Takeaways:
1. **Forking and Pull Requests** are essential for contributing to open-source or collaborative projects.
2. **Code reviews** should focus on providing constructive feedback to improve code quality.
3. **Merge conflicts** can be resolved locally before pushing changes back to the repository.
4. **Branch permissions** help enforce quality control by restricting who can modify critical branches.
5. **Rebase** keeps the history linear, while **merge** preserves the branching structure.

### Practical Exercise:
1. Fork a repository, create a branch, make changes, and submit a pull request.
2. Review a pull request, leave comments, and approve or request changes.
3. Resolve a merge conflict in a pull request, then rebase the branch before merging.
