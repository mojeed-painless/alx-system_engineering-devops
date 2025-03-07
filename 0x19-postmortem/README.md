Issue Summary
On March 6, 2025, from 11:15 AM to 1:45 PM WAT, our primary API service experienced a partial outage, causing degraded performance and intermittent failures for approximately 35% of users. Customers reported increased latency and frequent timeouts while attempting to access core functionalities. The root cause was an unexpected memory leak in the application server, leading to excessive resource consumption and eventual service crashes.

Timeline
11:15 AM WAT - Monitoring alert detected a spike in API response times and error rates.
11:20 AM WAT - Engineers began investigating logs and metrics, noticing high memory usage on multiple application servers.
11:30 AM WAT - An initial assumption was that a sudden increase in traffic was causing resource exhaustion.
11:45 AM WAT - Traffic shaping measures were applied, but the issue persisted, indicating another root cause.
12:00 PM WAT - Escalated to the backend engineering team for deeper investigation.
12:15 PM WAT - Memory profiling identified a specific API endpoint leaking memory due to inefficient object handling.
12:45 PM WAT - A temporary fix was deployed to restart affected application servers periodically to free up memory.
1:15 PM WAT - A permanent patch was developed and tested in a staging environment.
1:45 PM WAT - The patch was deployed, resolving the issue. Monitoring confirmed normal performance.

Root Cause and Resolution
The issue stemmed from an inefficient memory allocation pattern in a newly deployed API endpoint responsible for processing large datasets. A caching mechanism failed to release unused objects, leading to continuous memory consumption until the application server crashed.

To resolve this:
Engineers identified and corrected the faulty memory allocation logic.
A patch was deployed to ensure proper memory cleanup and garbage collection.
Additional memory profiling tools were enabled to catch similar issues in future deployments.
Corrective and Preventative Measures
Improvements:
Improve internal testing to include memory profiling for new deployments.
Enhance monitoring alerts to detect memory leaks earlier.
Implement automated server scaling to handle unexpected failures more gracefully.

Tasks:
Patch the affected API endpoint to optimize memory usage.
Add automated memory profiling in CI/CD pipelines.
Set up alerts for abnormal memory consumption trends.
Conduct an internal review to ensure other services are not vulnerable to similar issues.
Provide additional training for engineers on debugging memory-related issues.

By implementing these measures, we aim to prevent similar outages and improve system resilience moving forward.

