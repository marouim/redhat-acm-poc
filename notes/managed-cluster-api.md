```
oc get ManagedCluster

NAME            HUB ACCEPTED   MANAGED CLUSTER URLS   JOINED   AVAILABLE   AGE
eks-test        true                                  True     True        2d19h
local-cluster   true                                  True     True        69d
```

Ajouter un label a un cluster en utilisant l'API kubernetes

```
oc label ManagedCluster eks-test testing=fromcli
managedcluster.cluster.open-cluster-management.io/eks-test labeled
```

Le label est ensuite visible depuis la console ACM 




