You don’t want to hit a website from the same IP address repeatedly—that’s just asking for a ban, and it's very easy to ban an IP. A trick I found useful was setting up cheap EC2 instances or whatever provider you use, each running Playwright. You need distributed IPs and EC2 instances (or the equivalent).

***But here’s the key: separate your discovery infrastructure from your actual scraping.***

In other words, find your "targets" using one set of tools, then scrape using another. This keeps you from getting flagged too early and helps you stay under the radar.