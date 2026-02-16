# System Architecture Documentation

## Overview

The AI-First Engineering Training System is built entirely on GitHub Agentic Workflows, creating a self-contained, interactive learning platform within a GitHub repository.

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                         GitHub Repository                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌────────────────────┐        ┌─────────────────────────────┐  │
│  │  User Creates      │        │  user-onboarding.md         │  │
│  │  Onboarding Issue  │───────>│  - Parse profile            │  │
│  │  (training:new-user│        │  - Create Discussion        │  │
│  │   label)           │        │  - Init repo-memory         │  │
│  └────────────────────┘        │  - Add labels               │  │
│           │                    └─────────────────────────────┘  │
│           │                                │                     │
│           │                                ▼                     │
│           │                    ┌─────────────────────────────┐  │
│           │                    │  GitHub Discussion Created  │  │
│           │                    │  - "🎓 [User]'s Journey"    │  │
│           │                    │  - Welcome message          │  │
│           │                    │  - XP system explained      │  │
│           │                    └─────────────────────────────┘  │
│           │                                │                     │
│           │                                ▼                     │
│           │                    ┌─────────────────────────────┐  │
│           └───────────────────>│  Repo-Memory (Git-backed)   │  │
│                                │  users/[handle]/profile     │  │
│                                │  - Level, XP, badges        │  │
│                                │  - Skills, progress         │  │
│                                └─────────────────────────────┘  │
│                                                                   │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │            Learning Hub Manager (AI Mentor)                 │ │
│  │                                                              │ │
│  │  Triggers: discussion_comment: created                      │ │
│  │                                                              │ │
│  │  Actions:                                                    │ │
│  │  - Load user profile from repo-memory                       │ │
│  │  - Answer questions                                          │ │
│  │  - Provide personalized guidance                            │ │
│  │  - Suggest next challenges                                   │ │
│  │  - Update progress metrics                                   │ │
│  │  - Celebrate achievements                                    │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                │                                  │
│                                ▼                                  │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │            Specialized Coaches (On-Demand)                  │ │
│  │                                                              │ │
│  │  @prompt-coach         - Advanced prompting techniques      │ │
│  │  @workflow-architect   - Workflow design & debugging        │ │
│  │  @ethics-advisor       - Responsible AI use                 │ │
│  │  @transformation-mentor- Change management                  │ │
│  │                                                              │ │
│  │  Trigger: discussion_comment with @mention                  │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                                                   │
│  ┌────────────────────┐        ┌─────────────────────────────┐  │
│  │  User Requests     │        │  challenge-creator.md       │  │
│  │  Challenge         │───────>│  - Parse request            │  │
│  │  (creates issue or │        │  - Generate challenge       │  │
│  │   asks mentor)     │        │  - Create PR with content   │  │
│  └────────────────────┘        │  - Add labels               │  │
│                                └─────────────────────────────┘  │
│                                            │                     │
│                                            ▼                     │
│                                ┌─────────────────────────────┐  │
│                                │  Challenge PR Created       │  │
│                                │  - Objectives & tasks       │  │
│                                │  - Resources & examples     │  │
│                                │  - Acceptance criteria      │  │
│                                │  - XP reward info           │  │
│                                └─────────────────────────────┘  │
│                                            │                     │
│                                            ▼                     │
│                                ┌─────────────────────────────┐  │
│                                │  User Works on Challenge    │  │
│                                │  - Writes code/docs         │  │
│                                │  - Pushes to PR branch      │  │
│                                │  - Closes PR when ready     │  │
│                                └─────────────────────────────┘  │
│                                            │                     │
│                                            ▼                     │
│  ┌────────────────────┐        ┌─────────────────────────────┐  │
│  │  PR Closed         │        │  challenge-grader.md        │  │
│  │  (submission)      │───────>│  - Review submission        │  │
│  │                    │        │  - Score against rubric     │  │
│  │                    │        │  - Calculate XP earned      │  │
│  └────────────────────┘        │  - Update repo-memory       │  │
│                                │  - Check level-ups/badges   │  │
│                                │  - Post feedback            │  │
│                                │  - Comment on discussion    │  │
│                                └─────────────────────────────┘  │
│                                            │                     │
│                                            ▼                     │
│                                ┌─────────────────────────────┐  │
│                                │  Repo-Memory Updated        │  │
│                                │  + XP earned                │  │
│                                │  + Challenge completed      │  │
│                                │  + Skills improved          │  │
│                                │  + Possible level-up        │  │
│                                │  + New badges               │  │
│                                └─────────────────────────────┘  │
│                                                                   │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │            Achievement Tracker (Daily)                      │ │
│  │                                                              │ │
│  │  Triggers: schedule: daily                                  │ │
│  │                                                              │ │
│  │  Actions:                                                    │ │
│  │  - Load all user profiles                                   │ │
│  │  - Check for level-ups                                      │ │
│  │  - Award new badges                                         │ │
│  │  - Generate weekly reports (Mondays)                        │ │
│  │  - Send motivation to inactive users                        │ │
│  │  - Post progress updates to discussions                     │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                                                   │
│  ┌────────────────────────────────────────────────────────────┐ │
│  │            Industry Insights Curator (Weekly)               │ │
│  │                                                              │ │
│  │  Triggers: schedule: weekly                                 │ │
│  │                                                              │ │
│  │  Actions:                                                    │ │
│  │  - Research AI/engineering trends via web-fetch/search      │ │
│  │  - Curate relevant content                                  │ │
│  │  - Post weekly digest to all user discussions               │ │
│  │  - Personalize based on user level & interests              │ │
│  │  - Suggest deep-dive challenges on trends                   │ │
│  └────────────────────────────────────────────────────────────┘ │
│                                                                   │
└─────────────────────────────────────────────────────────────────┘
```

## Workflow Interactions

### User Onboarding Flow
1. User creates issue with `training:new-user` label
2. **user-onboarding** workflow:
   - Parses profile data
   - Creates GitHub Discussion
   - Writes initial profile to repo-memory
   - Adds labels to issue
   - Posts welcome comment
   - Closes issue

### Learning Flow
1. User comments on their Discussion
2. **learning-hub-manager** workflow:
   - Loads user profile from repo-memory
   - Interprets question/request
   - Provides personalized response
   - Updates engagement metrics
   - May trigger challenge creation

### Challenge Flow
1. User requests challenge (via mentor or direct issue)
2. **challenge-creator** workflow:
   - Generates appropriate challenge for level
   - Creates PR with full challenge content
   - Labels PR with `training:challenge` + `user:[handle]`
3. User works on challenge and closes PR
4. **challenge-grader** workflow:
   - Reviews submission against criteria
   - Scores using rubric
   - Calculates XP (50-100% of max)
   - Updates repo-memory with results
   - Posts detailed feedback on PR
   - Comments on discussion with summary
   - Suggests next challenge

### Specialized Coaching Flow
1. User mentions coach (e.g., @prompt-coach) in discussion
2. Respective coach workflow:
   - Detects mention via discussion_comment trigger
   - Loads user context from repo-memory
   - Provides expert domain guidance
   - Posts response to discussion

### Automated Maintenance
1. **achievement-tracker** (daily):
   - Processes all users
   - Awards badges
   - Checks level-ups
   - Sends weekly reports (Mondays)
   - Motivates inactive users

2. **industry-insights-curator** (weekly):
   - Researches current trends
   - Curates relevant content
   - Posts to all active users
   - Personalizes by level/interests

## Data Storage

### Repo-Memory Schema

```
repo-memory/
├── users/
│   ├── [github-handle-1]/
│   │   └── profile
│   │       {
│   │         "user_id": "string",
│   │         "name": "string",
│   │         "level": 1-5,
│   │         "xp": 0-10000+,
│   │         "badges": ["badge-name", ...],
│   │         "challenges_completed": ["challenge-id", ...],
│   │         "challenges_in_progress": ["challenge-id", ...],
│   │         "skills": {
│   │           "prompt_engineering": 0-100,
│   │           "agentic_workflows": 0-100,
│   │           "ai_code_review": 0-100,
│   │           "agent_orchestration": 0-100,
│   │           "ai_mentoring": 0-100
│   │         },
│   │         "profile": { ... },
│   │         "learning_style_effectiveness": {},
│   │         "last_active": "ISO-8601",
│   │         "completion_rate": 0.0-1.0,
│   │         "onboarded_date": "ISO-8601"
│   │       }
│   ├── [github-handle-2]/
│   │   └── profile
│   └── ...
```

### GitHub Resources Used

- **Issues**: Onboarding form, challenge requests
- **Discussions**: Personal learning hubs
- **Pull Requests**: Challenge submissions
- **Labels**: Workflow routing (`training:*`, `user:*`)
- **Comments**: Mentor feedback, grades, discussions

## Security Model

### Permissions
All workflows use **read-only permissions** except for safe-outputs:
- `contents: read` - Read repository files
- `issues: read` - Read issues
- `discussions: read` - Read discussions
- `pull-requests: read` - Read PRs

### Safe-Outputs (Write Operations)
All write operations use gh-aw safe-outputs:
- `create-discussion` - Create user learning hubs
- `add-labels` - Add workflow routing labels
- `add-comment` - Post feedback and guidance
- `close-issue` - Close onboarding issues
- `create-pull-request` - Create challenge PRs
- `create-issue` - Request challenge creation

### No Direct Write Permissions
Workflows NEVER have direct write permissions. All writes go through safe-outputs which:
- Validate all inputs
- Prevent injection attacks
- Log all operations
- Enforce limits (max per run)

## Scalability

### Single User
- Minimal resource usage
- Workflows only trigger for user's events
- Repo-memory is lightweight (JSON files)

### Multiple Users
- Each user has isolated Discussion
- Repo-memory scales linearly
- Scheduled workflows process all users efficiently
- Parallel challenge submissions supported

### Performance
- Workflows compile to optimized GitHub Actions
- Repo-memory uses git for efficient storage
- No external dependencies required
- Runs entirely on GitHub infrastructure

## Extensibility

### Adding New Workflows
1. Create new `.md` file in `.github/workflows/`
2. Define trigger, permissions, safe-outputs
3. Write agent instructions
4. Compile with `gh aw compile`

### Adding New Challenges
1. Create challenge content in `challenges/level-X/`
2. Update challenge-creator with new templates
3. Add to resource documentation

### Adding New Badges
1. Update achievement-tracker logic
2. Update user profile schema
3. Document in getting-started guide

### Adding New Skills
1. Add to profile schema in repo-memory
2. Update grading rubrics in challenge-grader
3. Create challenges that exercise new skills

## Monitoring

### User Activity
- `last_active` timestamp in profile
- Comment frequency in discussions
- Challenge completion rate
- Streak tracking

### System Health
- Workflow run status (GitHub Actions)
- Error logs in workflow runs
- Completion rates
- User engagement metrics

## Disaster Recovery

### Data Backup
- Repo-memory is git-backed (automatic backups)
- Discussions persist in GitHub
- All content in repository is versioned

### Recovery Procedures
1. Restore repository from GitHub backup
2. Repo-memory data in git history
3. Discussions remain intact
4. Re-compile workflows if needed

## Future Enhancements

### Potential Additions
- Team competitions and leaderboards
- Peer review challenges
- Real-time collaboration features
- Integration with external learning platforms
- Mobile-friendly progress dashboard
- Slack/Discord notifications
- Custom certificate generation
- Video content integration

### Considered But Not Implemented
- Complex state machines (kept simple)
- External databases (git-backed is sufficient)
- Webhook integrations (not needed initially)
- Custom UI (GitHub UI is adequate)
