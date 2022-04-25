# CAS-project
The website design for CAS project marine debris, describing the importance that relate to individuals ignorer to emphasize the importance.
name: Website green-o-meter

on:
  push:
    branches: main

jobs:
  update-gist:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@master
        with:
          persist-credentials: false
          fetch-depth: 0
      - name: green-website
        uses: filiptronicek/green-action@main
        env:
          URL: https://dev.to #Your measured URL
      - name: Commit files
        run: |
          git config --local user.email "action@github.com"
          git config --local user.name "GitHub Action"
          git commit -m "Update carbon image" -a
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: main #Change this to master, or any other branch to which the changes should be pushed
