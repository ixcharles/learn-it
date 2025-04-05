
# Troubleshooting and Optimization in Git

This course covers techniques for troubleshooting common Git issues, recovering lost commits, and optimizing repositories for performance and efficiency.

## Table of Contents

1. [Resolving Merge Conflicts](#resolving-merge-conflicts)
2. [Git Debugging and Recovering Lost Commits](#git-debugging-and-recovering-lost-commits)
3. [Optimizing Repository History and Reducing Repo Size](#optimizing-repository-history-and-reducing-repo-size)
4. [Using Reflog to Recover Data](#using-reflog-to-recover-data)
5. [Advanced Git Log Analysis (`git log`, `git blame`, `git bisect`)](#advanced-git-log-analysis-git-log-git-blame-git-bisect)

---

## Resolving Merge Conflicts

Merge conflicts occur when Git can't automatically reconcile changes between two branches. Here's how to resolve them.

### Steps:
1. **Identify Conflicts**: Git marks the conflicting files with conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
2. **Resolve**: Manually edit the conflicted files to combine the changes.
3. **Stage Changes**: After resolving conflicts, stage the files using `git add`.
4. **Commit**: Complete the merge with `git commit`.

**Example:**
```bash
git merge feature-branch
# Git will show conflict markers in conflicting files
# Edit and resolve the conflicts, then:
git add conflicted-file.txt
git commit -m "Resolved merge conflicts"
```

---

## Git Debugging and Recovering Lost Commits

If commits are accidentally lost, you can often recover them using Git’s debugging features.

### Recovering Lost Commits:
1. **Using `git reflog`**: Git logs the history of your HEAD, allowing you to find lost commits.
2. **Undoing a Reset**: If you’ve accidentally reset to an earlier commit, use `git reflog` to recover the lost commit.

**Example:**
```bash
# View reflog and find the lost commit
git reflog
# Reset to the desired commit
git reset --hard <commit-hash>
```

---

## Optimizing Repository History and Reducing Repo Size

Repositories can grow large and inefficient over time. Here's how to optimize them.

### Optimize History:
- **Squash Commits**: Use `git rebase -i` to squash multiple commits into a single one, cleaning up your history.
- **Prune Unused Branches**: Delete branches you no longer need with `git branch -d branch-name`.

### Reducing Repo Size:
- **Remove Large Files**: Use `git filter-branch` or `BFG Repo-Cleaner` to remove large files from history.
- **Prune Unreachable Objects**: Use `git gc` (garbage collection) to clean up unnecessary objects and reduce repo size.

**Example (Squashing commits)**:
```bash
git rebase -i HEAD~5
# Mark commits for squashing
git push --force
```

---

## Using Reflog to Recover Data

The `git reflog` command provides a history of changes to your local branches and HEAD, making it invaluable for recovering lost work.

### How to Use Reflog:
1. **View Reflog**: Use `git reflog` to view a history of changes.
2. **Recover Lost Commits**: Find the commit hash of the lost commit and reset your branch to that commit.

**Example**:
```bash
git reflog
# Identify the commit you want to recover
git reset --hard <commit-hash>
```

---

## Advanced Git Log Analysis (`git log`, `git blame`, `git bisect`)

Git provides several commands for analyzing your commit history and debugging issues.

### `git log`:
Use `git log` to view the commit history. You can customize the output with flags like `--oneline`, `--graph`, and `--author`.

**Example**:
```bash
git log --oneline --graph --decorate
```

### `git blame`:
Use `git blame` to identify who last modified each line in a file. This is helpful for debugging issues and tracking down the origin of bugs.

**Example**:
```bash
git blame file.txt
```

### `git bisect`:
Use `git bisect` to find the commit that introduced a bug by performing a binary search over your commit history.

**Example**:
```bash
git bisect start
git bisect bad # Mark the current commit as bad
git bisect good <commit-hash> # Mark an earlier commit as good
# Git will check out a commit in between, and you continue marking it as good or bad
```

---

## Conclusion

### Key Takeaways:
1. **Merge Conflicts** can be resolved by manually editing conflicting files, staging, and committing the resolved changes.
2. **Git Debugging** helps recover lost commits using tools like `git reflog`.
3. **Optimizing Repository Size** involves squashing commits and removing large files from Git history.
4. **Reflog** is invaluable for tracking and recovering data that has been lost or overwritten.
5. **Git Log Analysis** with `git log`, `git blame`, and `git bisect` helps identify the history of changes and isolate issues.

### Practical Exercise:
1. Create a conflict by making different changes to the same file in two branches, then resolve the conflict.
2. Use `git reflog` to find and recover a lost commit.
3. Clean up a repository by squashing commits and removing large files using `git filter-branch`.
4. Use `git blame` to track down the origin of a bug in a file.
5. Perform a `git bisect` to identify the commit that introduced a bug.
