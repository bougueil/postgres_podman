## a yaml file for podman to run postgres

### kubernetes yaml file

```yaml
# Save the output of this file and use podman play kube this_file.yaml
#
# Created with podman-3.4.4
---
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: "2023-01-08T10:53:03Z"
  labels:
    app: my-postgres
  name: my-postgres_pod
spec:
  containers:
  - args:
    - postgres
    image: docker.io/library/postgres:12.13-alpine3.17
    name: my-postgres
    envFrom:
      - configMapRef:
          name: postgres-config
    ports:
    - containerPort: 5432
      hostPort: 5432
    securityContext:
      capabilities:
        drop:
        - CAP_MKNOD
        - CAP_NET_RAW
        - CAP_AUDIT_WRITE
    volumeMounts:
    - mountPath: /var/lib/postgresql/data
      name: 715972759c94853a05d8cca0b63f9fd783f4b4649ae77ddfa6449fe0cc00361f-pvc
  volumes:
  - name: 715972759c94853a05d8cca0b63f9fd783f4b4649ae77ddfa6449fe0cc00361f-pvc
    persistentVolumeClaim:
      claimName: 715972759c94853a05d8cca0b63f9fd783f4b4649ae77ddfa6449fe0cc00361f
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: postgres-config
  labels:
    app: postgres
data:
  POSTGRES_USER: postgres
  POSTGRES_PASSWORD: postgres
```
