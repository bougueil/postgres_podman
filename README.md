## a yaml file for podman to run postgres
without exhausting your laptop batteries too much.

```bash
# runs locally postgres on a pod
podman play kube my-postgres.yaml 

# inspect the container
podman exec -it my-postgres bash
$ psql -U postgres
postgres=# \l

# shutting down
podman play kube my-postgres.yaml --down
```