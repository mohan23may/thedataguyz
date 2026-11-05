# Pushing this to github.com/mohan23may/thedataguyz

Run these from this folder in PowerShell or Git Bash on your own machine
(your GitHub credentials live there; the assistant's sandbox has no network access to GitHub).

## If the repo is empty

    git init -b main
    git add -A
    git commit -m "Add The Data Guyz website"
    git remote add origin https://github.com/mohan23may/thedataguyz.git
    git push -u origin main

## If the repo already has commits

    git init -b main
    git remote add origin https://github.com/mohan23may/thedataguyz.git
    git fetch origin
    git reset --soft origin/main
    git add -A
    git commit -m "Replace site with new design"
    git push origin main

## Then turn on Pages

GitHub → repo → Settings → Pages → Build and deployment →
Source: "Deploy from a branch", Branch: `main`, Folder: `/ (root)` → Save.

For the custom domain, add a file named `CNAME` containing `thedataguyz.com`
and point the DNS at GitHub Pages.
