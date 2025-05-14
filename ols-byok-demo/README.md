# OpenShift Lightspeed BYOK Demo

This repository demonstrates the **Bring Your Own Knowledge (BYOK)** capability of OpenShift Lightspeed (OLS), which allows customers to ingest their internal OpenShift policies and standards into OLS so that AI responses reflect organization-specific practices.

## 📁 Structure

- `*.md` files: Represent different internal documents such as policies, standards, or architectural guidelines.
- `olsconfig-sample.yaml`: Sample OlsConfig resource to point OLS to ingest these files.

## 🧪 Demo Examples

### 1. Namespace Naming Policy
**Demo Question:**  
> “Can I create a namespace called `Dev-Team123` in OpenShift?”

**OLS Response with BYOK:**  
> According to your organization’s namespace policy, namespaces must start with `team-` and use lowercase letters only. `Dev-Team123` does not conform to this policy.

---

### 2. Security Context Constraint (SCC) Policy  
**Demo Question:**  
> “Can I run my pod with hostPath and UID 0?”

**OLS Response with BYOK:**  
> Your SCC policy prohibits use of hostPath and UID 0. Use the `restricted-custom` SCC as defined by your security team.

---

### 3. Node Labeling Strategy  
**Demo Question:**  
> “How do I ensure my ML pods only run on ML nodes?”

**OLS Response with BYOK:**  
> Use the node selector:
```yaml
nodeSelector:
  node-role.kubernetes.io/ml: "true"
```

---

### 4. Resource Quotas  
**Demo Question:**  
> "What is my company's policy on resource quota?”

**OLS Response with BYOK:**  
> Your namespace has a max memory quota of 16Gi. You must request approval via Jira for exceeding this limit.

---

### 5. Internal Registry Usage  
**Demo Question:**  
> "what is my company's policy on using Docker Hub?”

**OLS Response with BYOK:**  
> External registries like Docker Hub are blocked. Please use `quay.mycompany.com/nginx` or mirror the image.

---

### 6. Logging Standards  
**Demo Question:**  
> "What is my company policy on writing logs?”

**OLS Response with BYOK:**  
> Logs must be in structured JSON and written to stdout/stderr only for Fluentd collection.

---

### 7. Deployment Strategy Policy  
**Demo Question:**  
> “what is my company's policy on deployment strategy ?”

**OLS Response with BYOK:**  
> Recreate strategy is disallowed. Please use RollingUpdate for production deployments.

---

## 🛠️ Usage

To integrate these with OLS:
1. Host the `.md` files publicly (GitHub raw URL or S3).
2. Update your `OlsConfig` CR with these URLs.
3. Deploy the OlsConfig to your cluster running OpenShift Lightspeed.



---

### 8. Pod Autoscaling Policy  
**Demo Question:**  
> "What is my company policy on HPA?”

**OLS Response with BYOK:**  
> According to your organization’s autoscaling policy, only CPU-based HPA is allowed by default in production. Memory-based or custom metrics require benchmarking and prior approval.
