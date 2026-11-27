## What is ETCD

<https://etcd.io/>

- A distributed key-value data store which stores the state of the system and objects
- Use Raft protocol to  coordinate the data access in distributed setup
- You can influence the way the API Server is using etcd via a number of options at start-up time. --etcd-servers List
  of etcd servers to connect with (scheme://ip:port)
- Kubernetes stores its objects in etcd either as a JSON string or in Protocol Buffers(“protobuf” for short) format


