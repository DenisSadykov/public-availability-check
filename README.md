# Availability check

Generic HTTPS availability checks with a status-only callback. Configuration is provided through repository secrets: `MONITOR_ENDPOINTS_JSON`, `MONITOR_CALLBACK_URL`, `MONITOR_CALLBACK_TOKEN`. No response bodies, endpoint URLs, tokens, artifacts, or caches are printed or uploaded. Only aggregate counts appear in logs.

The workflow uses a standard Linux runner, Python standard library, no third-party actions, no checkout and no repository write permissions. Only scheduled and manual runs receive secrets; pull requests cannot trigger it.

The schedule requests a run every five minutes, offset from the hour. GitHub schedules are best effort: runs may be delayed or dropped. Public repository schedules are disabled after 60 days without repository activity and require maintenance. Standard public runners are free; no larger runners, artifact storage or paid services are used. A successful callback is required before calling monitoring operational.
