# Patch Notes

## Summary

I reviewed the Task Tracker frontend, Spring Boot backend, and SQL reference files and fixed four high-impact issues.

1. Fixed SQL `AND`/`OR` precedence so archived tasks are excluded and search/status filters apply correctly.
2. Removed an artificial backend delay that caused unnecessary latency and contributed to stale responses.
3. Fixed frontend request lifecycle handling so stale responses cannot overwrite newer results and loading/error states are handled correctly.
4. Reset pagination to page 1 whenever the search query or status filter changes.

## What I did not change

I did not rewrite the application architecture, add dependencies, modify seeded task data, or change UI styling. I also left lower-priority issues such as unlimited `pageSize`, wildcard escaping, and development-only H2 console exposure unchanged to keep the patch focused.

## Biggest remaining risk

The backend still performs pagination in memory rather than at the database level. This is acceptable for the small seeded dataset but could become inefficient as the dataset grows.

## Tools / AI used

I used VS Code, PowerShell/curl, Maven, the browser, and AI assistance to inspect the code, identify issues, validate behavior, and review the patch.