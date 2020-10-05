# How to disable Metrics in OpenShift?
See: https://github.com/openshift/cluster-version-operator/blob/master/docs/dev/clusterversion.md



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
