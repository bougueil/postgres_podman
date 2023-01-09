## a yaml file for podman to run postgres
without exhausting your laptop batteries too much.

```bash
# runs postgres on a pod (locally)
podman play kube my-postgres.yaml 

# shutting down
podman play kube my-postgres.yaml --down
```