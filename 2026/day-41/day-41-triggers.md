# Task-1
## pr-check.yaml
``` bash
name: pr-check
on:
  pull_request:
    types: [opened , synchronize]
    branches: [main]
jobs:
  pr:
    runs-on: ubuntu-latest
    steps:
      - name: print PR branch name
        run: echo "pr check running for branch ${{ github.head_ref }}"
```
# Task-2
## schedule.yaml
``` bash
---
name: Schedule
on:
  schedule:
    - cron: 0 0 * * *
jobs:
  schedule-job:
    runs-on: unbuntu-latest
    steps:
      - name: run a scheduled script
        run: echo "this job runs on a schedule at midnight UTC everyday"
```
### Cron experssion for every monday at 9 am:- 0 9 * * 1
# Task-3
### manual.yml
``` bash
---
name: Manual
on:
  workflow_dispatch:
    inputs:
      environment:
        type: choice
        options:
          - staging
          - production
jobs:
  print_input:
    runs-on: ubuntu-latest
    steps:
      - name: prints inputs
        run: echo "${{ github.event.inputs.environment }}"
```

