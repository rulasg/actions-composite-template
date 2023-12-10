# Actions Composite Template

Composite action template to learn and seed other actions.

## Calling the action

This workflow will run the action as a step to prepare the runner to run tests.

```yaml
name: Call Action Composite Template

on:

  # Run as check on push request
  push:

  # Run as check on pull request
  pull_request:

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

permissions:
  # To run test we only need to read the repository
  contents: read

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      # Setup TestingHelper for later use
      - name: Call Action Composite Template with no input
        uses: rulasg/actions-composite-template@v1

        # Setup TestingHelper for later use
      - name: Call Action Composite Template with input
        uses: rulasg/actions-composite-template@v1
        with:
          who-to-greet: 'rulasg'
```

## Calling the reusuable workflow

This workflow will run the reusable workflow

```yaml

name: Reusable Test Workflow
on:
  pull_request:
  workflow_dispatch:

permissions:
  # To run test we only need to read the repository
  contents: read

jobs:
  # This workflow contains a single job that will call a reusable workflow
  call-reusable-testinghelper-worfklow:
    uses: rulasg/actions-composite-template/.github/workflows/testinghelper-workflow.yaml@main
```
