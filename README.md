# circassian-status

A tiny outside check for Circassian App. Every 10 minutes GitHub's own servers check whether the app's
server answers, and publish the result as `status.json` (branch `status`, also on GitHub Pages):

```json
{"v":1,"api":"ok","name":true,"ip":true,"at":"2026-11-19T12:00:00Z"}
```

The app reads it only when it can't reach its server itself, to tell "this network won't let the app
in" apart from "the server is down". `api` turns `down` only after two failed runs in a row (each run
tries both addresses three times), so one blip on GitHub's side never says the server is down.
