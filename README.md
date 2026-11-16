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
 
## Finding matches
Paste a grade link (the Play Cricket grade page URL) or ID into Find a match. It lists every match in the grade, filterable by round and team. Tap a completed match to load it. Grades and your chosen team are remembered in the browser. You can also paste a full match link into the match field and it extracts the ID.
 
Every match type with ball data can be loaded. For One Day matches, overs are pre-filled from the result (the larger of the two teams' overs bowled). Check it for games that were shorter or longer. For multi-day matches the Overs box is cleared, which means no limit: the page shows runs needed instead of a required rate, and the tables list every innings. Enter an overs limit if the game had one.
 
## Known assumptions
- Wides and no-balls count as a ball in every over except the final one. See `counts()` in `index.html`. Confirmed on two matches only.
- The innings is over when wickets fallen reach batters minus 1. Set Batters to the side's actual number (default 11).
- Fixtures contain team names and anonymised player labels (Batter 1, Bowler 1), never real player names. Live mode shows the real names the feed provides, in the viewer's browser only. Keep fixtures anonymised if the repo is public.
 
