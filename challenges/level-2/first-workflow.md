# Level 2 Challenge: Create a Simple Agentic Workflow

**Level:** 2 | **XP Reward:** 200 | **Estimated Time:** 2 hours

## 🎮 Objective

Design and implement your first GitHub Agentic Workflow that automates a real task in a repository. You'll learn about triggers, safe-outputs, and writing effective agent instructions.

## 🧠 Skills Practiced

- Agentic workflow design
- YAML frontmatter configuration
- Agent instruction writing
- Tool selection
- Safe-outputs configuration

## 📋 Task

Create a GitHub Agentic Workflow that automatically triages new issues by:
1. Reading the issue title and description
2. Analyzing the content
3. Adding appropriate labels (bug, feature, documentation, question)
4. Adding a comment welcoming the user and summarizing the issue

## ✅ Acceptance Criteria

Your workflow should:
- [ ] Trigger on issue opened events
- [ ] Use proper permissions (read-only except for safe-outputs)
- [ ] Configure safe-outputs for adding labels and comments
- [ ] Include clear, actionable instructions for the AI agent
- [ ] Handle edge cases (empty descriptions, unclear issues)
- [ ] Compile successfully with `gh aw compile`

## 💡 Resources

- [GitHub Agentic Workflows Documentation](https://github.github.com/gh-aw/)
- [Safe Outputs Reference](https://github.github.com/gh-aw/reference/safe-outputs/)
- Example workflows in this repository (`.github/workflows/`)

## 🎯 Submission Instructions

1. Create your workflow file at `.github/workflows/issue-triager.md`
2. Compile it to generate the `.lock.yml` file
3. Include both files in your submission
4. Add a README explaining your design decisions
5. Close this PR when ready for review

## 🏆 Bonus Points

- Add priority assessment to the triage (+40 XP)
- Include automated issue routing to team members (+60 XP)
- Add sentiment analysis for urgent issues (+80 XP)
- Create unit tests for your workflow logic (+100 XP)
