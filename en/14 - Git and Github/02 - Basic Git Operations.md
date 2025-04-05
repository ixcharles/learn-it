
# Basic Git Operations

This course covers the essential Git operations that every developer should know, from creating repositories to managing branches and resolving conflicts.

## Table of Contents

1. [Creating and Managing Repositories](#creating-and-managing-repositories)
2. [Staging and Committing Changes](#staging-and-committing-changes)
3. [Viewing Changes](#viewing-changes)
4. [Undoing Changes](#undoing-changes)
5. [Git Branching Basics](#git-branching-basics)
6. [Merging Branches](#merging-branches)
7. [Resolving Merge Conflicts](#resolving-merge-conflicts)

---

## Creating and Managing Repositories

A repository in Git stores your project's files and their version history. To create and manage repositories:

- `git init`: Initializes a new Git repository in the current directory.
- `git clone <repo_url>`: Creates a copy of an existing repository from a remote source.

**Example:**
```bash
git init
git clone https://github.com/username/repo.git
```

---

## Staging and Committing Changes

- **Staging**: Add files to the staging area before committing.
  - `git add <file>`: Adds a file to the staging area.
- **Committing**: Save changes in the repository with a message.
  - `git commit -m "message"`: Records changes to the repository.

**Example:**
```bash
git add file.txt
git commit -m "Add file.txt with initial content"
```

---

## Viewing Changes

- `git diff`: Shows the differences between the working directory and the staging area.
- `git log`: Displays a history of commits in the repository.

**Example:**
```bash
git diff
git log
```

---

## Undoing Changes

- **Undo Staged Changes**: Move changes from the staging area back to the working directory.
  - `git reset <file>`: Unstages a file.
- **Undo Local Changes**: Revert changes in the working directory.
  - `git checkout -- <file>`: Discards changes in the working directory.

**Example:**
```bash
git reset file.txt
git checkout -- file.txt
```

---

## Git Branching Basics

Branching allows you to work on different versions of a project simultaneously.

- `git branch`: Lists, creates, or deletes branches.
- `git checkout -b <branch_name>`: Creates and switches to a new branch.

**Example:**
```bash
git branch
git checkout -b feature-branch
```

---

## Merging Branches

Merging combines the changes from one branch into another.

- `git merge <branch_name>`: Merges changes from the specified branch into the current branch.

**Example:**
```bash
git checkout main
git merge feature-branch
```

---

## Resolving Merge Conflicts

Merge conflicts occur when changes in different branches cannot be automatically merged.

- **Manual Conflict Resolution**: Git marks conflicting files. You must edit these files to resolve the conflicts.
- After resolving, add the resolved files to the staging area and commit.

**Example:**
```bash
git add conflict-file.txt
git commit -m "Resolved merge conflict"
```

---

## Conclusion

### Key Takeaways:
1. Repositories are created using `git init` or cloned with `git clone`.
2. Staging and committing changes ensures your code is saved in the repository.
3. Viewing changes with `git diff` and `git log` helps track progress.
4. Undoing changes can be done using `git reset` and `git checkout`.
5. Branching and merging are essential for working on features in isolation and combining work.
6. Merge conflicts are resolved by manually editing files and committing the resolution.

### Practical Exercise:
1. Create a new repository, add files, and commit changes.
2. Create a branch, make changes, and merge it back into the main branch.
3. Create a conflict between branches and resolve it manually.
