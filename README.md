
# Issue

After merging Release PR created by Release-Please, the logs will show:
```

```
and the process stops there, short of going through Gihut Release.

# Prerequisite

1. Github > Settings > Actions, check `Allow GitHub Actions to create and approve pull requests`.
1. Github > Settings > General, under `Pull Requests`, check `Allow squash merging Loading` and set default commit message to `Pull Request title and commit details`.

# Steps to reproduce

1. Make a change in projectA file
```bash
sed -i "s/ 123 456//" projectA/src/app.service.ts
git add projectA/src/app.service.ts
git commit -m "fix: fixed projectA getHello()."
sed -i "s/Learn React 123/Learn React Here/" projectB/src/App.js
git add projectB/src/App.js
git commit -m "fix: fixed projectB App."

git push
```

2. A Release PR should be created with the title `chore: release main` with the label `autorelease: pending`.
3. **Squash and Merge** Release PR.
4. Check the last run in Actions.