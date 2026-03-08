# Task-3
- on:
Defines the event that triggers the workflow, such as push, pull request, or schedule.

- jobs:
Contains the list of jobs that the workflow will execute.

- runs-on:
Specifies the type of runner (machine/OS) where the job will run, for example ubuntu-latest.

- steps:
A sequence of tasks executed inside a job.

- uses:
Used to run an existing GitHub Action from the marketplace or repository.

- run:
Executes a command or script directly in the runner's shell.

- name (on a step):
A readable label for the step, shown in the GitHub Actions logs to make the pipeline easier to understand.

# Task-5
When a pipeline fails, the workflow run shows a red ❌ status in the Actions tab, and the job stops at the step where the error occurred.
You can open the failed step logs to see the error message and exit code (like 127) which helps identify what command or script caused the failure.

#hello.yaml 
``` bash
---
name: Hello
on:
  push:
    branches:
      - main
jobs:
  greet:
    runs-on: ubuntu-latest
    steps:
      - name: checking out the code
        uses: actions/checkout@v4
      - name: prints hello
        run: echo "Hello from github actions"
      - name: prints date and time
        run: date
      - name: prints the name of the branch
        run: echo "The triggered branch name is ${{ github.ref_name }}"
      - name: listing the files in the repo
        run: ls -la
      - name: Print os name of the runner
        run: echo "The operating system is $RUNNER_OS"
```
