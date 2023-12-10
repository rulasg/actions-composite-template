# Actions Composite Template

Composite action template to learn and seed other actions.

## Calling the action

This workflow will run a job with a step that will call the action and a job that will call the resusable workflow that will call the action.

```yaml
name: Call Actions Composite Template

on: 
  workflow_dispatch:

jobs:
  ACT-call:
    name: Call to Actions Composite template
    runs-on: ubuntu-latest
    steps:
      - uses: rulasg/actions-composite-template@main
      - uses: rulasg/actions-composite-template@main
        with:
          who-to-greet: "Raúl"

  ACT-reusable:
    uses: rulasg/actions-composite-template/.github/workflows/actions-composite-template.yaml@main
```
