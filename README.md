# common-validating-policies

A collection of common ValidatingAdmissionPolicies to help enforce best practices within Kubernetes clusters

## Installation

All these policies make use of Kustomize and can either be installed all together or individually.

### Installing all policies

```sh
kubectl kustomize ./policies/ | kubectl apply -f -
```

### Installing individual policies

Example with the [block-latest-tag](./policies/block-latest-tag/) policy:

```sh
kubectl kustomize ./policies/block-latest-tag/ | kubectl apply -f -
```
