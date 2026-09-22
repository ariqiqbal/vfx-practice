
---

# Git Workflow – Effection Team

## 1. Selected Git Workflow and Rationale

### Selected Git Workflow

Our team will use **Trunk-Based Development** for the Space Invaders Visual Effects project.

Our team consists of **8 members**, with each member assigned to specific Visual Effects (VFX) features. Each member will work on their assigned feature using a separate short-lived branch.

The team will use the `main` branch as the main trunk of the project. Completed features will be integrated into `main` after testing and review.

### Rationale

We selected Trunk-Based Development because each team member has their own assigned feature to develop. Members can first develop and test their own features separately without affecting the stable version of the project.

If a feature does not work correctly, the changes can be modified or reverted before being integrated into the main project.

This workflow also allows our team to:

- Develop different VFX features in parallel.
- Practice using Git branches and repositories.
- Keep the `main` branch as the main integrated version of the project.
- Test individual features before integration.
- Reduce the risk of unfinished code affecting the main project.
- Frequently integrate completed features into the project.

---

# 2. Branch Strategy

Our team will use the following branch structure:

| Branch | Purpose |
|---|---|
| `main` | Main trunk containing the integrated and tested project |
| `feature/<feature-name>` | Individual member's branch for developing an assigned VFX feature |

### `main`

The `main` branch is the main trunk of our project.

It should contain the latest integrated version of the game that has been reviewed and tested.

Members should **not directly push unfinished work to `main`**.

### Feature Branches

Each team member will create a branch for their assigned feature.

For example:

```text
feature/bullet-enemy-impact
feature/barrier-impact
feature/player-damage
feature/life-glitch
feature/game-over
```

Each feature branch should focus on one specific VFX feature.

### When Branches Are Created

A feature branch is created when a team member starts working on a new assigned feature.

Example:

```bash
git checkout main
git pull origin main
git checkout -b feature/player-damage
```

### When Branches Are Merged

A feature branch can be merged into `main` when:

1. The assigned feature is completed.
2. The feature has been tested.
3. The feature does not break existing gameplay.
4. The changes have been reviewed.
5. Any merge conflicts have been resolved.

### When Branches Are Deleted

After the feature branch has been successfully merged into `main` and is no longer needed, the branch should be deleted.

This keeps the repository clean and prevents old branches from accumulating.

---

# 3. Commit Rules

Each commit should contain **one logical change or function**.

Since each member is responsible for a specific feature, commits should be focused rather than combining many unrelated changes into one commit.

For example, for a player damage feature:

```text
Commit 1: Add player damage visual effect
Commit 2: Add life reduction glitch effect
Commit 3: Connect damage effect to player hit event
```

Avoid commits such as:

```text
Update everything
Finish VFX
Changes
Final
```

### Commit Message Format

Our team will use:

```text
[FEATURE] Short description
```

Examples:

```text
[BULLET] Add enemy hit effect
[BARRIER] Add barrier impact particles
[PLAYER] Add player damage effect
[LIFE] Add life reduction glitch
[GAMEOVER] Add enemy collapse effect
```

The commit message should clearly describe the change made in that commit.

### Commit Rule

Team members should commit their work **frequently and logically** rather than putting all changes into one large commit at the end.

Each commit should represent a meaningful change that can be understood by other team members.

---

# 4. Pull Request and Code Review Rules

## Pull Request

A Pull Request should be opened when a member has completed and tested their assigned feature and the feature is ready to be integrated into `main`.

The Pull Request should include:

- Feature name.
- Description of the changes.
- Testing performed.
- Any known issues.
- Screenshots or a short video/GIF when appropriate for VFX.

Example:

```text
Feature branch:
feature/player-damage

        ↓ Pull Request

Team repository:
main
```

### Code Review

Before merging, the team leader or assigned reviewer should check:

- Whether the feature matches the requirement.
- Whether the VFX works correctly.
- Whether the feature affects existing gameplay.
- Whether the code is understandable.
- Whether the feature has been tested.
- Whether unnecessary changes are included.

If problems are found, the member should fix them on their branch and update the Pull Request.

### Approval

A Pull Request must receive **at least one review/approval from the team leader or assigned reviewer** before being merged into `main`.

### Direct Push to `main`

**Direct pushes to `main are not allowed for normal feature development.**

All completed features should go through the team's review/integration process.

This ensures that the team leader can control what enters the main project.

---

# 5. Merge Strategy

Our team will primarily use **Merge** to integrate completed feature branches into `main`.

### Merge

A feature branch will be merged after:

```text
Feature completed
       ↓
Feature tested
       ↓
Pull Request
       ↓
Code review
       ↓
Approved
       ↓
Merge into main
```

### Squash

Our team may use **Squash Merge** when a feature branch contains many small temporary commits, such as:

```text
fix
fix again
test
change
fix bug
```

These commits can be combined into one meaningful commit before entering `main`.

### Rebase

Rebase is not our primary merge strategy.

It may be used by a team member to update their own feature branch with the latest `main` before merging.

Team members should avoid rebasing a branch that is already being actively shared by other members.

---

## Merge Conflict Resolution

If a merge conflict occurs, the **member responsible for the feature branch** will be responsible for resolving the conflict.

The member should:

1. Identify the conflicting changes.
2. Discuss with the other member if the conflict involves their code.
3. Resolve the conflict.
4. Test the project after resolving it.
5. Update the Pull Request if necessary.
6. Ask the reviewer to check the changes again.

For conflicts involving important shared code, the team leader will help decide which implementation should be kept.

---

# 6. Overall Development Workflow

Our team's development process is:

### Step 1 — Assign Features

The 8 team members are assigned different VFX features.

Our planned VFX features include:

| Member | Feature |
|---|---|
| Member 1 | Bullet hits enemy |
| Member 2 | Bullet hits barrier |
| Member 3 | Player attacked by enemy |
| Member 4 | Player life reduction / glitch effect |
| Member 5 | Player destruction effect |
| Member 6 | Game Over enemy collapse effect |
| Member 7 | Environmental effects |
| Member 8 | VFX integration, cleanup and testing |

These assignments can be adjusted by the team depending on implementation difficulty.

### Step 2 — Update `main`

Before starting work, the member gets the latest version of the project:

```bash
git checkout main
git pull origin main
```

### Step 3 — Create Feature Branch

The member creates a branch for their assigned feature:

```bash
git checkout -b feature/player-damage
```

### Step 4 — Develop the Feature

The member implements the assigned VFX feature.

For example:

```text
Player attacked
      ↓
Damage detected
      ↓
Player flash/glitch effect
      ↓
Life decreases
```

### Step 5 — Commit Changes

The member makes small, meaningful commits:

```bash
git add .
git commit -m "[PLAYER] Add player damage effect"
```

### Step 6 — Test

The member tests the feature in the game.

The member should check:

- Does the VFX trigger at the correct time?
- Does it appear at the correct location?
- Does it disappear correctly?
- Does the game continue working?
- Does it interfere with other VFX?

### Step 7 — Push the Branch

When the feature is ready:

```bash
git push origin feature/player-damage
```

### Step 8 — Queue for Integration

The completed feature is placed in the team's integration queue.

The team leader/reviewer checks the Pull Request and reviews the feature.

### Step 9 — Review

If changes are required:

```text
Review
  ↓
Changes requested
  ↓
Developer fixes feature
  ↓
Push changes
  ↓
Review again
```

If approved:

```text
Approved
   ↓
Merge
```

### Step 10 — Integrate into `main`

The team leader merges the approved feature into `main`.

### Step 11 — Delete the Branch

After successful integration, the feature branch can be deleted if it is no longer needed.

### Step 12 — Next Feature

The team member updates their local `main` and starts their next assigned task.

---

# Overall Development Flow

```text
                  ┌─────────────────────┐
                  │   Assign Feature    │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Update latest main  │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Create Feature      │
                  │ Branch              │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Develop VFX Feature │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Small Meaningful    │
                  │ Commits             │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Test Feature        │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Push Feature Branch │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Pull Request /      │
                  │ Integration Queue   │
                  └──────────┬──────────┘
                             ↓
                  ┌─────────────────────┐
                  │ Code Review         │
                  └──────────┬──────────┘
                             ↓
                       ┌─────┴─────┐
                       │           │
                    Changes?     Approved
                       │           │
                       ↓           ↓
                  Fix Changes   Merge to
                       │          main
                       │           │
                       └─────┐     │
                             ↓     ↓
                           Review
                             │
                             ↓
                    ┌─────────────────┐
                    │ Delete Feature  │
                    │ Branch          │
                    └────────┬────────┘
                             ↓
                    ┌─────────────────┐
                    │   Next Feature  │
                    └─────────────────┘
```

---

## One thing I would change in your team's original idea

You said:

> "after done, push dekat team repo, then nanti leader yg akan push dekat main repo"

I'd change this slightly because **"push to team repo" and "push to main" can be confusing**.

Use this terminology in the document:

> **Each member develops their assigned feature on their own feature branch. After completing and testing the feature, they push the branch to the team repository and open a Pull Request to `main`. The team leader reviews the Pull Request and merges the approved changes into `main`.**

So the flow becomes:

```text
Member's branch
      ↓
Push branch
      ↓
Team repository
      ↓
Pull Request
      ↓
Leader review
      ↓
Merge
      ↓
main
```

That is much clearer for your lecturer.

### Also, your feature list

I would **not call "game over – all enemy collapsed after all 3 lives habis" a VFX requirement by itself**. Separate the **game logic** from the **visual effect**:

> **Game logic:** Player loses all 3 lives → Game Over state is triggered.  
> **VFX:** Player destruction animation → enemy collapse/explosion effect → transition to Game Over screen.

That makes your VFX team's responsibility much clearer and prevents your team from accidentally taking responsibility for the entire game-over logic.

And because your team wants to **practice repository/Git**, the branch → PR → leader review → merge process is useful even though Trunk-Based Development emphasizes frequent integration.
