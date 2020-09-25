# How to disable Metrics in OpenShift?

**version-patch.yaml**

	- op: add
	  path: /spec/overrides
	  value:
	  - kind: Deployment
	    group: apps/v1
	    name: cluster-monitoring-operator
	    namespace: openshift-monitoring
	    unmanaged: true

Patch ClusterVersion:

	oc patch clusterversion version --type json -p "$(cat version-patch.yaml)"
