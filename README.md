# Chase tracker
 
Live required-rate tracker for Play Cricket matches. Static site, no build step.
 
## Deploy on GitHub Pages
1. Create a repo and add `index.html` and the `fixtures/` folder at the root.
2. Repo Settings > Pages > Deploy from a branch > `main` / root.
3. Open `https://<user>.github.io/<repo>/`.
## Test locally
`python3 -m http.server` in this folder, then open http://localhost:8000. Replay mode loads the fixtures with `fetch`, which fails when the file is opened directly from disk.
 
## Live use
Pick Live, paste the match ID (the long string in the Play Cricket match URL), set the overs limit. It polls `/balls` every 60 seconds, the same as the feed's cache time.
 
## Known assumptions
- Wides and no-balls count as a ball in every over except the final one. See `counts()` in `index.html`. Confirmed on two matches only.
- The innings is over when wickets fallen reach batters minus 1. Set Batters to the side's actual number (default 11).
- Fixtures contain no player names. Keep it that way if the repo is public.
 
