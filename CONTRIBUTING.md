# Contributing Rules

Welcome to ai-agento! We are excited that you want to contribute.  
To keep our development process smooth and consistent, we follow **[GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)**.  

This document explains everything you need to know: from branch naming to commit messages, and from pushing changes to opening a PR.

---

## Table of Contents

1. [GitHub Flow Overview](#github-flow-overview)
2. [Branch Naming](#branch-naming)
3. [Commit Message Style](#commit-message-style)
4. [Step‑by‑Step Workflow](#stepbystep-workflow)
   - [1. Create a branch](#1-create-a-branch)
   - [2. Make changes and commit](#2-make-changes-and-commit)
   - [3. Push your branch to GitHub](#3-push-your-branch-to-github)
   - [4. Open a Pull Request](#4-open-a-pull-request)
   - [5. Review and merge](#5-review-and-merge)
5. [Example Walkthrough](#example-walkthrough)
6. [Additional Tips](#additional-tips)

---

## GitHub Flow Overview

GitHub Flow is a lightweight, branch‑based workflow that supports teams that deploy regularly.  
The core idea is:

- **Everything in `main` is always deployable.**
- **All work happens on feature branches** (branches created from `main`).
- **Changes are merged back via Pull Requests** after review.

There are no long‑lived development branches—only `main` and short‑lived feature branches.

---

## Branch Naming

To keep branches organised and meaningful, use the following naming pattern:


- **Type** describes the purpose of the branch. Common types:
  - `feat` – a new feature  
  - `fix` – a bug fix  
  - `docs` – documentation changes  
  - `style` – formatting, missing semicolons, etc. (no code change)  
  - `refactor` – code restructuring without changing behaviour  
  - `test` – adding or correcting tests  
  - `chore` – build process, tooling, or dependency updates  

- **Short‑description** is a few hyphen‑separated words that summarise the work (keep it under 50 characters).

**Examples:**
- `feat/user-authentication`
- `fix/login-error-message`
- `docs/api-endpoints`
- `refactor/database-connection`

> ⚠️ **Never** work directly on the `main` branch. Always create a branch from `main`.

---

## Commit Message Style

We follow **[Conventional Commits](https://www.conventionalcommits.org/)** to make our history readable and to enable automatic versioning and changelog generation.

A commit message must look like:


\<type>(\<scope>): \<subject>
\<BLANK LINE>
\<body>
\<BLANK LINE>
\<footer>


For most contributions, a simple one‑line commit is enough:


\<type>(\<scope>): \<subject>


- **`type`** – same as branch types (feat, fix, docs, style, refactor, test, chore).
- **`scope`** (optional) – the part of the codebase affected (e.g., `auth`, `api`, `ui`). Put it in parentheses.
- **`subject`** – a short, imperative description of the change (no period at the end).

**Examples of good commit messages:**
- `feat(auth): add OAuth2 login flow`
- `fix(api): handle empty response from payment service`
- `docs(readme): update installation instructions`
- `refactor(parser): simplify error handling logic`

---

## Step‑by‑Step Workflow

### 1. Create a branch

Always start from the latest `main` branch:


# Switch to main and pull the latest changes
git checkout main
git pull origin main

# Create and switch to your feature branch
git checkout -b feat/your-feature-name


### 2. Make changes and commit

Work on your changes, then stage and commit them with a meaningful message:


git add .
git commit -m "feat(module): implement new feature"


If you need to make several commits, that’s fine—they will be squashed later.

### 3. Push your branch to GitHub

Push the branch to the remote repository:


git push origin feat/your-feature-name


The first time you push, Git may suggest a command like:

git push --set-upstream origin feat/your-feature-name


### 4. Open a Pull Request

1. Go to your repository on GitHub.
2. You will see a banner suggesting to open a Pull Request for your recently pushed branch. Click **Compare & pull request**.
3. Fill in the PR title and description:
   - **Title** – concise summary of the change (e.g., `Add OAuth2 login`).
   - **Description** – explain what you did, why, and any relevant context (e.g., issue numbers).
4. Select the base branch (`main`) and the compare branch (your feature branch).
5. Add reviewers and assignees if needed.
6. Click **Create pull request**.

### 5. Review and merge

- Other team members will review your PR, leave comments, and request changes if necessary.
- You can continue pushing new commits to the same branch—the PR will update automatically.
- Once the PR is approved and all status checks (CI, tests) pass, it is ready to merge.

**Merge options:**

We use **“Squash and merge”** to keep the history of `main` clean and linear.  
All commits from your feature branch are squashed into a single commit when merged.  
This commit will have the title and description from your PR, making the history easy to read and understand.

After merging, the feature branch is deleted automatically (our repository is configured to do so).

---

## Example Walkthrough

Let’s walk through a complete example: adding a new feature “user profile picture upload”.

### 1. Create branch


git checkout main
git pull origin main
git checkout -b feat/profile-picture-upload


### 2. Make changes and commit

We add a new file `upload.py` and modify `profile.py`.  
Then we commit:


git add upload.py profile.py
git commit -m "feat(profile): add picture upload endpoint"


We later fix a small bug in the same branch:


git add upload.py
git commit -m "fix(upload): handle large files correctly"


### 3. Push


git push origin feat/profile-picture-upload


### 4. Open a PR

- Go to GitHub, click **Compare & pull request**.
- Title: `Add profile picture upload`
- Description:
  
  Closes #42.
  - Implements /upload endpoint
  - Validates file type and size
  - Stores image in cloud storage
  
- Create PR.

### 5. Review and merge

After approval and passing CI checks, click **Squash and merge**.  
The branch will be deleted automatically.  
Your changes are now in `main` and will be deployed.

---

## Additional Tips

- **Keep your branch short‑lived** – try to merge within a day or two. If you need longer, rebase periodically to stay up‑to‑date with `main`.
- **Use `git pull --rebase` to update your branch** – before pushing, it is good practice to incorporate upstream changes without creating merge commits in your feature branch. For example:
  
  git pull --rebase origin main
  
- **Write descriptive PR descriptions** – they help reviewers understand the context and become the squash commit message.
- **Link issues** – if your PR fixes an issue, mention `Closes #<issue-number>` in the PR description.
- **CI checks** – ensure all tests pass before requesting a review. Our `main` branch is protected and will not accept changes that break the build.
- **Ask for help** – if you are unsure about anything, just ask in the PR comments or on our team chat.

---

Thank you for contributing! By following these rules, we keep our project healthy and our collaboration effective.  
Happy coding! 🚀