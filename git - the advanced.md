
upstream - original repo
origin - your fork

- `git pull` pulls from somewhere unexpected
- `git push` goes to the wrong repo
- You’re working with forks or multiple remotes



update release-dev locally
`git switch release-dev`
`git pull origin release-dev`

Refresh feature branch `aoi-locations` from `release-dev`:
`git switch aoi-locations`
`git merge origin/release-dev`
`git push origin aoi-locations`

