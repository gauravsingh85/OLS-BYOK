# Node Labeling Strategy

Workload Types:
- ML Workloads → `node-role.kubernetes.io/ml=true`
- Infra Workloads → `node-role.kubernetes.io/infra=true`

Ensure all ML pods define:
```yaml
nodeSelector:
  node-role.kubernetes.io/ml: "true"
```
