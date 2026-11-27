## Flow from kubectl apply -f pod.yaml to object in etcd

- Get the version from http path (e.g. v1 or v1beta1)
- Create the empty object using Scheme in the right version
- JSON or protobuf decoder converts the payload into object
- Write requests are all applied to ETCD leader node

![flow](resources/kubectl-apply-flow.png)

## Flow from kubectl get pods

- Get request is sent to kube-apiserver
- kube-apiserver uses the ETCD client lib to talk to etcd cluster.
  [Implementation](https://github.com/kubernetes/apiserver/blob/master/pkg/storage/storagebackend/factory/etcd3.go#L110)
- ETCD3 client performs a quorum read by default to make sure always the latest value gets returned. ETCD2 needs to pass
  in a flag `quorum-read=true` to achieve the quorum read
