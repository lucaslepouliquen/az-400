# Configuring and Managing Repositories

## Table of Contents
- [Working With Large Repositories](#working-with-large-repositories)
- [Configuring Git Tags](#configuring-git-tags)
- [Purging Data From Source Control](#purging-data-from-source-control)
- [Recovering Data From Source Control](#recovering-data-from-source-control)

---

## Working With Large Repositories

### Understanding the Challenges

Two main challenges with large repos are extensive commit histories and the presence of large binary files, both of which can slow down Git operations.

**Main Challenges:**
- Extensive commit histories
- Presence of large binary files

### Optimizing History

Use **Shallow Cloning** to clone only recent snapshots of your history, which can significantly speed up cloning time.

**Command Example:**
```bash
git clone --depth [number-of-commits] [repository-url]
```

**Parameters:**
- Replace `[number-of-commits]` with the desired history depth
- Replace `[repository-url]` with the URL of the Git repository

---

### Handling Large Files

#### Git Large File Storage (LFS)

Implement Git Large File Storage (LFS) to manage binary files separately from text files, streamlining the workflow.

**To get started with Git LFS:**
```bash
git lfs install
```

**What is Git LFS?**

A Git extension used to manage large files and binary data. It replaces large files such as audio samples, videos, datasets, and graphics with text pointers inside Git, while storing the file contents on a remote server.

#### Git-fat

Another tool that can be used to handle large files in Git repositories. It allows you to manage large files without checking them into the Git history, helping to keep the repository size down.

---

### Scalar

Scalar is a set of tools and extensions for Git that enables it to work efficiently with very large repositories by optimizing repository functions.

**What is Scalar?**
- A .NET Core application optimized for both Windows and macOS
- Enhances Git to handle very large repositories efficiently
- Utilized by Microsoft for the Windows and Office repositories

#### Advanced Git Features Enabled by Scalar

1. **Partial Clone** - Jumpstart your work by only downloading necessary Git objects initially
2. **Background Prefetch** - Automate the fetching of updates, reducing manual fetch times
3. **Sparse-Checkout** - Streamline your workspace by only checking out the directories you need
4. **File System Monitor** - Improve performance by monitoring file changes without scanning the entire workspace
5. **Commit-Graph** - Make browsing commit history snappier with optimized commit walks
6. **Multi-Pack-Index** - Quickly find objects within your repository, even with many pack-files
7. **Incremental Repack** - Reorganize packed data more efficiently for better Git operations

#### Setting Up Scalar

**Step 01: Register your repo with Scalar**
```bash
scalar register
```

**Step 02: Take a break from Scalar optimizations**
```bash
scalar pause
```

**Step 03: Stop Scalar management for a repo**
```bash
scalar unregister
```

#### Daily Use Commands

**Run maintenance tasks automatically:**
```bash
scalar run all
```

**Clone with Scalar to optimize from the start:**
```bash
scalar clone [repository-url]
```

---

## Configuring Git Tags to Organize Source Control Repository

### The Role of Git Tags

Tags in Git serve as landmarks, signifying important commits, typically used for version releases or highlighting significant changes.

### Creating Tags

#### Lightweight Tag
```bash
git tag [tag-name]
```

**Example:**
```bash
git tag v2.0
```

#### Annotated Tag
```bash
git tag -a [tag-name] -m "[tag-message]"
```

**Example:**
```bash
git tag -a v2.1 -m "Release 2.1 with enhanced features"
```

### Listing Tags

To view all tags in the repository:
```bash
git tag
```

### Pushing Tags to Remote

#### Single Tag
```bash
git push origin [tag-name]
```

**Example:**
```bash
git push origin v2.0
```

#### All Tags
```bash
git push origin --tags
```

### Using Tags for Organization

#### Checkout to a Tag
```bash
git checkout [tag-name]
```
Temporarily switch to the state of the repo at the tag for inspection or hotfixes.

#### Sorting Tags by Version
```bash
git tag --sort=v:refname
```
Lists tags in a version-aware order, helpful for navigating through versions.

---

### Organizing Your Repository Using Git Tags in Azure Repos

Git tags serve as fixed reference points in your project's history, commonly marking release points or significant changes in Azure Repos.

**Creating, listing, and pushing of tags:**
- Can be done using the `git tag` command as shown before
- Can also be created and managed through the Azure DevOps web interface for enhanced visual management

---

### Organizing Your Repository Using Git Tags in GitHub Releases

#### Releases and Tags in GitHub

**GitHub Releases** are official snapshots of your project, typically associated with a version number.

**Each release is based on a Git tag**, which marks a specific point in your repo's history.

**Tags** help you to organize and identify specific states of your code in the source control, aiding in tracking progress and changes.

#### Creating a Release Tag

To mark a new version of your software, you can create a tag using the GitHub CLI:
```bash
gh release create [tag-name]
```

**Example:**
```bash
gh release create v1.0.0
```

#### Adding Details to Your Release

To include a title and release notes, enhance your command:
```bash
gh release create [tag-name] --title "[release-title]" --notes "[release-notes]"
```

**Example:**
```bash
gh release create v1.0.0 --title "Initial Release" --notes "Features included in this release..."
```

---

## Purging Data From Source Control

**Purging:** the process of cleaning up your codebase by removing unnecessary or sensitive files.

### Reasons for Purging Files

1. To shrink the repository size for optimized performance
2. To eliminate large files that were committed by mistake
3. To expunge files containing sensitive information like passwords or API keys

### Tools for Repository Cleanup

#### Git filter-repo
A versatile tool that allows for selective rewriting of repository history

#### BFG Repo-Cleaner
A simpler, faster alternative to filter-branch for cleaning up data

### Example Usage

#### Reduce repo size by deleting large or unnecessary files:
```bash
bfg --delete-files yourfile.ext
```

**OR**
```bash
git filter-repo --path archive.tar.gz --invert-paths
```

#### Remove sensitive content from your history:
```bash
bfg --replace-text passwords.txt
```

**OR**
```bash
git filter-repo --replace-text passwords.txt
```

### Post-Purge Steps

**Step 01: Force push the changes**
```bash
git push --force
```

**Step 02: Re-clone Alert**

Alert collaborators to re-clone the repository to ensure everyone's local copy is in sync with the revised history.

---

## Recovering Data From Source Control

### Recovering Data Using Git Commands

#### Restoring Deleted Commits

**Find the lost commit via the reflog:**
```bash
git reflog
```

**Checkout the commit if you know the hash:**
```bash
git checkout [commit-hash]
```

#### Reverting Changes

**Undo the last commit, keeping changes:**
```bash
git reset --soft HEAD~1
```

**Discard the last commit's changes:**
```bash
git reset --hard HEAD~1
```

#### Recovering a Deleted Branch

**Locate the last commit of the deleted branch:**
```bash
git reflog
```

**Recreate the branch from the commit:**
```bash
git checkout -b [new-branch-name] [commit-hash]
```

---

### Recovering Data From Source Control Using Azure Repos

You can use git commands to perform recovery actions if you are using Git in Azure Repos.

From the UI, you can restore deleted branches by simply searching for the name of the branch.

---

## Resources

Visit [www.kodekloud.com](https://www.kodekloud.com) to learn more.

---

© Copyright KodeKloud