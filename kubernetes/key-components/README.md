## What are admission controllers

- **Gatekeeper** that intercept (authenticated) API requests and may change the request object or deny the request altogether.
  For example, when a namespace is deleted and subsequently enters the Terminating state, the NamespaceLifecycle admission
  controller is what prevents any new objects from being created in this namespace.
- Among the more than 30 admission controllers shipped with Kubernetes, two take a special role because of their nearly
  limitless flexibility - **`ValidatingAdmissionWebhooks`** and **`MutatingAdmissionWebhooks`**.
  This approach decouples the admission controller logic from the Kubernetes API server, thus allowing users to implement
  custom logic to be executed whenever resources are created, updated, or deleted in a Kubernetes cluster.
![admission controller phases](resources/admission-webhook-phrases.png)

![validating-webhook-flow](resources/validating-webhook-flow.png)

## What is ETCD

<https://etcd.io/>

- A distributed key-value data store which stores the state of the system and objects
- Use Raft protocol to  coordinate the data access in distributed setup
- You can influence the way the API Server is using etcd via a number of options at start-up time. --etcd-servers List
  of etcd servers to connect with (scheme://ip:port)
- Kubernetes stores its objects in etcd either as a JSON string or in Protocol Buffers(“protobuf” for short) format


