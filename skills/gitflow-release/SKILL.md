---
name: gitflow-release
description: Git Flow release automation with idempotent step execution. This skill should be used when users want to release a version using git-flow, finish a feature and create a release tag, or resume a previously interrupted release process. Typical triggers include "发布版本", "release", "finish feature and release", "继续发布".
---

# Git Flow Release Skill

Automate the git-flow release process (feature finish → release branch → release finish → tag → push) with **idempotent execution**. Each step checks the current git state before acting, safely skipping completed steps so the process can resume from any interruption point.

## Usage

The user provides two parameters:
- **feature_name**: Feature branch name without `feature/` prefix (e.g. `631_unread_stats`)
- **version**: Semver version number, with or without `v` prefix (e.g. `1.2.3` or `v1.2.3`)

## Pre-flight Checks

Before starting, verify all of the following. Report all failures at once rather than stopping at the first one:

1. Run `git flow version` to confirm git-flow is installed
2. Read gitflow config values — run all of these:
   - `git config --get gitflow.prefix.feature` → FEATURE_PREFIX
   - `git config --get gitflow.prefix.release` → RELEASE_PREFIX
   - `git config --get gitflow.branch.master` → MASTER_BRANCH
   - `git config --get gitflow.branch.develop` → DEVELOP_BRANCH
   - `git config --get gitflow.prefix.versiontag` → VERSIONTAG_PREFIX (may be empty, that's OK)
3. Compute TAG = `${VERSIONTAG_PREFIX}${VERSION}` (strip leading `v` from user input first, e.g. `v1.2.3` → `1.2.3`)
4. Verify version matches semver: `X.Y.Z` or `X.Y.Z-pre.N`
5. Verify the working tree is clean: `git diff --quiet && git diff --cached --quiet`
6. Run `git fetch --tags` to sync remote state

## Execution Steps (Idempotent)

Execute steps 1–6 in order. **Before each step, check the current state to determine if the step is already done. If done, report it as skipped and move to the next step.**

### Step 1: Feature Finish

**State check:** Run `git show-ref --verify refs/heads/${FEATURE_PREFIX}${feature_name}`. If the feature branch does NOT exist, it was already merged → skip this step.

**Action:** Run:
```bash
GIT_MERGE_AUTOEDIT=no git flow feature finish "${feature_name}"
```

**On merge conflict:** Stop execution, tell the user to resolve conflicts manually, then re-invoke this skill to continue.

### Step 2: Create Release Branch

**State check:** Run `git show-ref --verify refs/heads/${RELEASE_PREFIX}${VERSION}`. If the release branch already exists → switch to it with `git checkout ${RELEASE_PREFIX}${VERSION}` and skip creation.

**Action:** From the develop branch, run:
```bash
git checkout "${DEVELOP_BRANCH}"
git checkout -b "${RELEASE_PREFIX}${VERSION}"
```

### Step 3: Release Finish

**State check:** Two conditions indicate this step is done:
- The release branch `${RELEASE_PREFIX}${VERSION}` no longer exists (deleted by release finish), AND
- The tag `${TAG}` exists locally (`git tag -l "${TAG}"` returns non-empty)

If both are true → skip this step.

**Action:** Run:
```bash
GIT_MERGE_AUTOEDIT=no git flow release finish -m "${TAG}" "${VERSION}"
```

**Post-action verification:** Confirm the tag exists: `git tag -l "${TAG}"`. If missing, report the error and suggest the user check `gitflow.prefix.versiontag` config.

**On merge conflict:** Stop execution, tell the user to resolve conflicts manually, then re-invoke this skill to continue.

### Step 4: Push Tag

**State check:** Run `git ls-remote --tags origin "refs/tags/${TAG}"`. If the tag already exists on remote → skip.

**Action:** Run:
```bash
git push origin "${TAG}"
```

### Step 5: Push Master

**State check:** Run `git fetch origin ${MASTER_BRANCH}` then compare `git rev-parse ${MASTER_BRANCH}` with `git rev-parse origin/${MASTER_BRANCH}`. If they are equal → skip.

**Action:** Run:
```bash
git checkout "${MASTER_BRANCH}"
git push origin "${MASTER_BRANCH}"
```

### Step 6: Push Develop

**State check:** Run `git fetch origin ${DEVELOP_BRANCH}` then compare `git rev-parse ${DEVELOP_BRANCH}` with `git rev-parse origin/${DEVELOP_BRANCH}`. If they are equal → skip.

**Action:** Run:
```bash
git checkout "${DEVELOP_BRANCH}"
git push origin "${DEVELOP_BRANCH}"
```

## Output Format

For each step, report status clearly:

- **Skipped**: `[Step N] ✓ 已跳过 — {reason}` (e.g. "feature 分支已合并")
- **Executing**: `[Step N] 正在执行 — {description}`
- **Success**: `[Step N] ✓ 完成 — {description}`
- **Failed**: `[Step N] ✗ 失败 — {error}`, then stop and report how to resume

After all 6 steps, print a final summary showing the tag name, current branch, and all steps' status.

## Error Recovery Guidance

When a step fails:
1. Report which step failed and why
2. Tell the user what to fix (e.g. resolve merge conflicts, check network)
3. Tell the user they can simply re-invoke this skill with the same parameters to resume — completed steps will be automatically skipped
