# This is for copying from one repo to another

### Note: Only do this if you want the new repo to have all the branches from the old repo. Your new repo will have contributors of whoever contributed on the old repo

Can follow [Repo Setup.pdf](Repo%20Setup.pdf) but with one minor change to make life easier:

Instead of manually checking out all the branches (step 4-6) manually as stated in the pdf, run

```bash
git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote" || true; done 2>/dev/null
```

After it finishes running, verify by doing

```bash
git branch -a
```

To make sure for every `remotes/origin/` branch, there's one locally. If a branch is missing, you can manually do

```bash
git checkout $branch_name
```

Note: if you're missing `remotes/origin/develop`, just do `git checkout develop` don't include `remotes/origin`

The rest is the same as in the pdf
