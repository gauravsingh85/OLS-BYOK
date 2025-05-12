# Deployment Strategy Policy

- **Staging:** Use Canary strategy with Istio traffic shifting
- **Production:** Use RollingUpdate
- **Disallowed:** Recreate strategy (causes downtime)

Example RollingUpdate:
```yaml
strategy:
  type: RollingUpdate
```
