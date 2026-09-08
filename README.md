# Payment ACH

Clickable prototypes for ACH payment flows, organized **one folder per
screen** to make design review focused and easy to comment on.

## Structure

Each screen lives in its own top-level folder, self-contained (its own
`index.html`, and any CSS/JS it needs) so it can be opened directly in a
browser with no build step and no dependency on any other screen's folder:

```
payment-ach/
├── failure-acknowledgement/
│   └── index.html
├── <next-screen>/
│   └── index.html
└── ...
```

Open a screen locally:

```bash
open failure-acknowledgement/index.html
```

## Workflow: one PR per screen

`main` is protected — every screen is added via its own pull request, not
pushed directly:

1. Branch off `main`: `git checkout -b screen/<screen-name>`
2. Add the new `<screen-name>/` folder with its prototype.
3. Push and open a PR. Review happens on that PR, scoped to just that one
   screen.
4. Merge once approved.

This keeps review focused (one screen's diff at a time, not a pile of
unrelated screens) and keeps `main` always in a reviewed, mergeable state.

## Adding a new screen

```bash
git checkout main
git pull
git checkout -b screen/your-screen-name
mkdir your-screen-name
# build the prototype in your-screen-name/index.html
git add your-screen-name/
git commit -m "feat: add your-screen-name prototype"
git push -u origin screen/your-screen-name
gh pr create
```
