# **Installation using HELM**

### Sidecar Installation

#### Commands:

**The commands used for updating helm:**

`helm repo add istio https://istio-release.storage.googleapis.com/charts`

`helm repo update`

**Install Istio:**

`helm install istio-base istio/base -n istio-system --set defaultRevision=default --create-namespace`

`helm install istiod istio/istiod -n istio-system --wait`

**Implementation:**

`kubectl label namespace <your-namespace-name> istio-injection=enabled`

You can rollout restart for all the workloads in that namespace and the sidecar will be injected in that namespace

### Ambient Mode

#### Commands:

**The commands used for updating helm:**

`helm repo add istio https://istio-release.storage.googleapis.com/charts`

`helm repo update`

**Install Istio:**

`helm install istio-base istio/base -n istio-system --set defaultRevision=default --create-namespace`

`kubectl get crd gateways.gateway.networking.k8s.io &> /dev/null || { kubectl apply -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.2.0/standard-install.yaml; }`

`helm install istiod istio/istiod --namespace istio-system --set profile=ambient --wait`

`helm install istio-cni istio/cni -n istio-system --set profile=ambient --wait`

`helm install ztunnel istio/ztunnel -n istio-system --wait`

**Implementation:**

`kubectl label namespace <your-namespace-name> <label for ambient mode>`

You can rollout restart for all the workloads in that namespace and the sidecar will be injected in that namespace

**For Further queries refer docs:**

https://istio.io/latest/docs/
