name: Generate Contribution Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches: [main]

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 15
    steps:
      - name: Generate Snake Animation
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          # Tip (optional): to make the snake/dots match your #F97316 theme
          # instead of GitHub's default green, replace the dark line with:
          # dist/github-contribution-grid-snake-dark.svg?color_snake=%23f5f5f5&color_dots=%23161616,%237c2d12,%23c2410c,%23ea580c,%23F97316
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        continue-on-error: true

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
          keep_history: false
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
