# tms-uptime

Off-box uptime monitor for https://trendmarketshifts.com.

Every 5 minutes a GitHub Action checks `/api/v1/health` and the homepage
(3 tries, 20s apart). If the site is down, the run fails and GitHub notifies
the repo owner (email + GitHub mobile push): once when it goes down, then once
an hour while it stays down. `status.json` records the current state, the last
outage and a weekly heartbeat.

It lives in its own public repo because public repos run standard Actions
runners for free, so it never uses the private repo's included minutes.

Send a test alert: Actions tab -> uptime -> Run workflow -> tick "force_fail".
