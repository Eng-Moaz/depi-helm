# depi-helm

Helm chart for the library app (frontend, auth, catalog, postgres).

```text
library/
  Chart.yaml
  values.yaml        general defaults
  values-dev.yaml    namespace library-dev, 1 replica each
  values-prod.yaml   namespace library-prod, 2 replicas for auth, catalog, frontend
  templates/         configmaps/ deployments/ services/
```

Install:

```bash
helm upgrade --install library library -n library-dev  --create-namespace -f library/values-dev.yaml
helm upgrade --install library library -n library-prod --create-namespace -f library/values-prod.yaml
```

Images come from `ghcr.io/eng-moaz/library-*` (see `depi-auth`, `depi-catalog`, `depi-frontend`).
