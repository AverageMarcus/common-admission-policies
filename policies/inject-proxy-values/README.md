# inject-proxy-values

This policy injects `HTTP_PROXY` env vars into all containers launched

## Parameters

The [`params.yaml`](./params.yaml) file contains a ConfigMap that will be used for the values of the proxy env vars. You will first need to modify these to what is needed in your environment.

## Examples

Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

Result (excess omitted for brevity)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
    env:
    - name: HTTP_PROXY
      value: http://proxy.proxy.svc:3128
    - name: HTTPS_PROXY
      value: http://proxy.proxy.svc:3128
    - name: NO_PROXY
      value: .svc.cluster,.svc.cluster.local,svc,127.0.0.1,localhost
```
