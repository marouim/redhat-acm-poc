https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.2/html/web_console/web-console#queries-in-the-console



1.3.1. Search customization
When you install Red Hat Advanced Cluster Management, the product is configured to persist the data in-memory to a file system. The StatefulSet search-redisgraph deploys the Redisgraph pod, which mounts the persistent volume named persist. If your cluster has a defined default storage class, the search component creates a Persistent Volume Claim (PVC) of 10Gi on the default storage class. If a default storage class does not exist in your cluster, search saves the index in an empty directory (emptyDir).

You can customize the storage settings for search by creating the searchcustomization CR. Search customization is namespace-scoped and located where search is installed in the hub cluster. View the following example of the search customization CR:

apiVersion: search.open-cluster-management.io/v1alpha1
kind: SearchCustomization
metadata:
  name: searchcustomization
  namespace: open-cluster-management
spec:
  persistence: true
  storageClass: gp2
  storageSize: 12Gi
Run the following command to view search customization CRD:

oc get crd searchcustomizations.search.open-cluster-management.io -o yaml
You can disable persistence by updating the persistence flag to false in the customization CR, which turns off saving search index to the file system. A status for persistence can be retrieved from the search operator (searchoperator) CR. Run the following command to view search operator CR: oc get searchoperator searchoperator -o yaml.

