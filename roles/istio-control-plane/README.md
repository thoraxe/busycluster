This role requires that a parameter/variable `api_url` point to the OpenShift API URL.

If you get into a weird state you can force cleanup:

```bash
oc delete project istio-operator
oc delete project istio-system
oc delete crd/installations.istio.openshift.com 
oc delete roles.rbac.authorization.k8s.io/istio-operator
oc delete rolebindings.rbac.authorization.k8s.io/default-account-istio-operator
oc delete clusterrolebindings.rbac.authorization.k8s.io/default-account-istio-operator-cluster-role-binding
oc get clusterrolebindings.rbac.authorization.k8s.io -A | grep -e "^istio" | awk '{print $1}' | xargs oc delete clusterrolebindings.rbac.authorization.k8s.io
oc get secret -A | grep istio | awk -F\  '{print "oc delete -n " $1 " secret/" $2}' | while read LINE; do $LINE; done
```