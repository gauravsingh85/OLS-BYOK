# OpenShift SCC Usage Policy

All workloads must use the `restricted-custom` SCC:
- Must run as non-root
- Must not request privileged escalation
- HostPath volumes are not allowed
- Only whitelisted UIDs are permitted
