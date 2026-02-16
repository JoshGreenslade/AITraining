# Level 3 Challenge: Multi-Agent System Design

**Level:** 3 | **XP Reward:** 300 | **Estimated Time:** 4 hours

## 🎮 Objective

Design a coordinated multi-agent system where multiple workflows work together to accomplish a complex task. You'll learn about agent coordination, state management, and workflow orchestration.

## 🧠 Skills Practiced

- Multi-agent system design
- Workflow coordination
- Repo-memory for state management
- Advanced safe-outputs
- Complex trigger patterns

## 📋 Task

Create a PR review assistance system with 3 coordinating agents:

### Agent 1: PR Analyzer
- Triggers on PR opened
- Analyzes the PR for size, complexity, and risk
- Stores analysis in repo-memory
- Assigns reviewers based on expertise

### Agent 2: Code Quality Checker
- Triggers on PR synchronize
- Reviews code for quality issues
- Checks against best practices
- Posts inline comments on issues

### Agent 3: Review Coordinator
- Triggers on PR review submitted
- Tracks review status
- Reminds reviewers if needed
- Merges when approved

## ✅ Acceptance Criteria

Your system should:
- [ ] Include all 3 workflow files
- [ ] Use repo-memory to share state between agents
- [ ] Properly coordinate handoffs between agents
- [ ] Handle race conditions and concurrent events
- [ ] Include comprehensive agent instructions
- [ ] Compile successfully without errors
- [ ] Include architecture documentation

## 💡 Resources

- [Multi-Agent Patterns](https://github.github.com/gh-aw/patterns/multi-agent/)
- [Repo-Memory Documentation](https://github.github.com/gh-aw/reference/repo-memory/)
- [Workflow Orchestration Guide](https://github.github.com/gh-aw/guides/orchestration/)

## 🎯 Submission Instructions

1. Create your 3 workflow files
2. Compile all workflows
3. Create an architecture diagram (can be ASCII art or image)
4. Write detailed documentation explaining:
   - How the agents coordinate
   - State management strategy
   - Error handling approach
   - Example scenarios
5. Close this PR when ready for review

## 🏆 Bonus Points

- Add a 4th agent for automated testing (+100 XP)
- Implement rollback on failed checks (+120 XP)
- Add metrics and reporting dashboard (+150 XP)
- Create automated tests for agent coordination (+200 XP)
