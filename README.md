# CS-744-Course-Project

## Heron on Kubernetes

#### Link to docs

https://apache.github.io/incubator-heron/docs/getting-started/

https://github.com/apache/incubator-heron/tree/master/deploy/kubernetes/minikube

#### Link to Heron tracker

http://localhost:8001/api/v1/namespaces/default/services/heron-tracker:8888/proxy/topologies

#### Link to Heron UI

http://localhost:8001/api/v1/namespaces/default/services/heron-ui:8889/proxy

#### Link to Heron API Server

http://localhost:8001/api/v1/namespaces/default/services/heron-apiserver:9000/proxy/

http://localhost:8001/api/v1/namespaces/default/services/heron-apiserver:9000/proxy/api/v1/version

#### Start proxy

```sh
kubectl proxy -p 8001
```

#### Set Service URL

```sh
heron config kubernetes \
set service_url http://localhost:8001/api/v1/namespaces/default/services/heron-apiserver:9000/proxy
```


#### Submit Topology

```sh
heron submit kubernetes \
~/.heron/examples/heron-streamlet-examples.jar \
com.twitter.heron.examples.streamlet.WindowedWordCountTopology \
WindowedWordCountTopology
```

```sh
heron submit kubernetes ~/.heron/examples/heron-api-examples.jar \
com.twitter.heron.examples.api.AckingTopology acking
```

## SSH commands

#### Parallel scp

```sh
pscp -h slaves -O StrictHostKeyChecking=no src /users/szhong
```

#### Parallel ssh

```sh
pssh -i -h slaves -O StrictHostKeyChecking=no cmd
```

