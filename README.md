# GitHub Activities

Updates `README.md` with the recent GitHub activity of a user.

---

## 📊 Recent GitHub Activity

<!--START_SECTION:activity-->
<!--END_SECTION:activity-->

---

## 🚀 How to Use

### Step 1: Add Comments to Your README

Add the following comments to your `README.md` where you want the activity to appear:

```markdown
<!--START_SECTION:activity-->
<!--END_SECTION:activity-->
```

### Step 2: Create Workflow File

Create `.github/workflows/update-readme.yml`:

```yml
name: Update README with GitHub Activity

on:
  schedule:
    - cron: '0 */6 * * *'  # Run every 6 hours
  workflow_dispatch:       # Allow manual trigger

permissions:
  contents: write         # Write permission to commit to repository

jobs:
  update-readme:
    runs-on: ubuntu-latest
    name: Update README with recent GitHub activity
    
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      
      - name: Update README with GitHub Activity
        uses: duchuy1452/github-activities@main
        with:
          USERNAME: ${{ github.repository_owner }}
          MAX_LINES: '5'
          COMMIT_MSG: '🚀 Update README with latest GitHub activity'
        env:
          ACTIVITY_TOKEN: ${{ secrets.ACTIVITY_TOKEN }}
```

## ⚙️ Configuration Options

| Input | Description | Default Value | Required |
|-------|-------------|---------------|----------|
| `USERNAME` | GitHub username | `${{ github.repository_owner }}` | No |
| `MAX_LINES` | Maximum number of activity lines | `5` | No |
| `COMMIT_MSG` | Commit message for updates | `:zap: Update README with the recent activity` | No |
| `README_PATH` | Path to README file | `./README.md` | No |

## 🎯 Features

- 🔄 Automatically updates with recent GitHub activities
- ⚡ Supports commits, PRs, issues, stars, forks, and more
- 🎨 Customizable activity count and commit messages
- 📝 Flexible README path support
- 🚀 Uses Node.js 20 for better performance
