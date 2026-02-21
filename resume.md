

What you built → How complex it was → Why it mattered → Measurable result

- No clear scale beyond 1k DAU
- No quantified performance engineering
- No distributed systems depth
- No backend system ownership at scale
- No algorithmic signal


- Reduced Google Distance Matrix API usage by batching destination requests (25 per call), cutting latency and external API cost for route calculations in a shuttle booking system.
- Designed and built image upload for support tickets (S3, presigned URLs, access checks), enabling media in chat and improving support workflows.
- architectured an event driven serverless data pipeline in Azure, made the UI and backend for setting/getting configs from database
- Designed and implemented a FastAPI backend for a SaaS platform with role-based access, PostgreSQL, and 50+ REST endpoints.
- Integrated Razorpay payments and Zoho Books for automated invoice generation and email delivery on credit purchases.
- Built async notification pipeline with AWS SQS, SES, and SNS; background workers for email, SMS, and scheduled message reminders.

phoenix
- created a cron job to calculate the invoices and get it auto approved from gst

bookmyband
- full stack app next js + fastapi