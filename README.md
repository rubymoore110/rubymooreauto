# auto-green
name: ci

on:
  push:
    branches:
      - master
  schedule:
    - cron: "* */78 * * *"

jobs:
  autogreen:
    runs-on: ubuntu-latest
    steps:
      - name: Clone repository
        uses: actions/checkout@v2

      - name: Auto green
        run: |
          git config --local user.email "cleland1432803776@icloud.com"
          git config --local user.name "AndersonHJB"
          git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
          git pull --rebase
          git commit --allow-empty -m "a commit a day keeps your girlfriend away"
          git push
```
