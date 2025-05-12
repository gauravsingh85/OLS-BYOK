# Image Registry Policy

- Use `quay.mycompany.com` for all image pulls.
- External registries like `docker.io`, `gcr.io` are blocked in production.
- CI pipelines must validate image source before deployment.

Example allowed image:
```
quay.mycompany.com/team/app:latest
```
