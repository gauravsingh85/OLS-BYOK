# Logging Requirements

- Format: JSON
- Required fields: `env`, `service`, `request_id`
- Output: stdout and stderr only
- Use middleware to inject missing fields if necessary

Sample log:
```json
{
  "env": "prod",
  "service": "payments-api",
  "request_id": "abc-123",
  "message": "payment processed"
}
```
