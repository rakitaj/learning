# Practical Alerting from Time-Series Data

## Core learnings
You need the time-series data and identifying dimensions about it. Ex: The latency per request, tagged with each web server, region, time of day it was made. This helps identify factors in common for the requests with high latency.

- White box monitoring - Emitting data from the application and host
- Black box monitoring - Hitting the application like a customer would

## Definitions
- Time-series arena: Fixed size block of memery where time-series data is stored
- Horizon: Time between the oldest and newest entry
- TSDB: Time-series database

## Notes
### Collection of exported data
HTTP is a robust protocol. Scraping servers over it works well.

Move the in-memory time-series data to a TSDB at whatever schedule you need.