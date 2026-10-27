# Risks and open questions (fictional)

| ID | Risk or question | Impact | What would resolve it | Owner | Resolution |
| --- | --- | --- | --- | --- | --- |
| Q1 | Does the notification service retry failed sends? | Offers silently lost (R2) | Read its runbook; test with the service down | Priya Nair | Resolved 30 Jul: retries 3× with backoff; email rate-limited to 1/min per member (see implementation return) |
| Q2 | What share of members have push off? | Size of the email path | Device-registration table query | Aoife Brennan | Resolved 30 Sep: 22% at pilot sites → promoted to product brain |
| Q3 | Do managers want member names on the waitlist view? | Privacy (R6) | Ask 3 managers; check privacy policy | Aoife Brennan | Resolved 25 Jul: counts are enough; names declined for privacy |
| Q4 | Daylight-saving night: does 07:00 fire once? | Duplicate or missing offers (R5) | Time-freeze test across the DST boundary | Implementer | Resolved: done-when check C9 |
