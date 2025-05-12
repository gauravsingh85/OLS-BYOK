# Pod Autoscaling Policy

For production workloads:
- **HPA is mandatory**
- **Metric**: Use CPU utilization by default
- **Replicas**: Minimum 2, maximum 10
- **Memory-based scaling** or **custom metrics** require performance benchmarking and explicit approval

Sample HPA:
```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: myapp-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: myapp
  minReplicas: 2
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 75
```
