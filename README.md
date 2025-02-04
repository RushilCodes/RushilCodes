name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"  # Runs daily at midnight
  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2
      - name: Generate Snake Contribution Graph
        uses: Platane/snk@v2
        with:
          github_user_name: "RushilCodes"
          outputs: |
            github-contribution-grid-snake.svg?color_snake=true
      - name: Commit and Push
        uses: stefanzweifel/git-auto-commit-action@v4
        with:
          commit_message: "Updated contribution snake graph"
