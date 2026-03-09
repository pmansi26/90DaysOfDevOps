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
# Task-4
### matrix.yaml
``` bash
---
name: Matrix
on:
  push:
    branches:
      - main
jobs:
  python_version:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
         python-version: [ "3.10" , "3.11" , "3.12" ]
         os: [ "windows-latest" , "ubuntu-latest" ]
    steps:
      - name: Setup python
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
      - name: check python version
        run: python --version
      - name: check operating system
        run : echo "Running on ${{ runner.os }}"
```
- Total number of jobs after adding os :- 6
# Task-5
``` bash
---
name: Matrix
on:
  push:
    branches:
      - main
jobs:
  python_version:
    runs-on: ${{ matrix.os }}
    strategy:
      fail-fast: false
      matrix:
         python-version: [ "3.10" , "3.11" , "3.12" ]
         os: [ "windows-latest" , "ubuntu-latest" ]
         exclude:
           - os: windows-latest
             python-version: "3.10"
    steps:
      - name: Setup python
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
      - name: check python version
        run: python --version
      - name: check operating system
        run : echo "Running on ${{ runner.os }}"
```

**fail-fast in GitHub Actions (Matrix Strategy)**

**fail-fast: true (default)**
If any job in the matrix fails, GitHub **immediately cancels the remaining running or queued matrix jobs** to save time and resources.

**fail-fast: false**
Even if one job fails, **all other matrix jobs continue running** until they finish.


