### Step 1: Grant Permissions to Fluentd

Save these manifests in the rbac.yml separating them by the ---delimiter and create all resources in bulk. 

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: fluentd
namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRole
metadata:
  name: fluentd
  namespace: kube-system
rules:
- apiGroups:
- ""
  resources:
  - pods
  - namespaces
  verbs:
  - get
  - list
  - watch
---
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1beta1
metadata:
  name: fluentd
roleRef:
  kind: ClusterRole
  name: fluentd
  apiGroup: rbac.authorization.k8s.io
subjects:
- kind: ServiceAccount
  name: fluentd
  namespace: kube-system

```
```cli
kubectl create -f rbac.yml
serviceaccount “fluentd” created
clusterrole.rbac.authorization.k8s.io “fluentd” created
clusterrolebinding.rbac.authorization.k8s.io “fluentd” created
```
### Step 2: 
