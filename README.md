# readme-chart-report-example
![chart](./chart-report.png)

## Workflow

```
name: Quick Chart Report
on:
  issues:
    types: [opened, closed]
  pull_request:
    types: [opened, closed]
    branches: [main]
  push:
    branches: [main]
  schedule:
    - cron: '0 0 * * *'
jobs:
  generate-chart:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          ref: main
          token: ${{secrets.TOKEN}}
      - uses: minuth/quickchart-report@main
        with:
          token: ${{secrets.TOKEN}}
```
This workflow specifies the events that will trigger the workflow, including opening and closing issues and pull requests to the main branch, pushes to the main branch, and a scheduled job that runs once a day. The generate-chart job specifies that the action will run on an Ubuntu environment, and includes the steps to checkout the repository and use the Quick Chart Report action to generate chart images and display them in the README file.
