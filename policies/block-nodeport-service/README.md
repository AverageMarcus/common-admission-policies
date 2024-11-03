# block-nodeport-service

This policy prevents the use of NodePort type Services that could possibly be used to bypass NetworkPolicies.

## Examples

### 🚫 Blocked

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nodeport-service
spec:
  type: NodePort
  selector:
    app.kubernetes.io/name: example
  ports:
    - name: http
      port: 80
      targetPort: 80
```

### ✅ Valid

```yaml
apiVersion: v1
kind: Service
metadata:
  name: clusterip-service
spec:
  type: ClusterIP
  selector:
    app.kubernetes.io/name: example
  ports:
    - name: http
      port: 80
      targetPort: 80
```
