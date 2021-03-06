# Template Service Broker Operator

The template service broker gives the service catalog visibility into the default Instant App and Quickstart templates that have shipped with OpenShift Container Platform since its initial release. The template service broker can also make available as a service anything for which an OpenShift Container Platform template has been written, whether provided by Red Hat, a cluster administrator or user, or a third-party vendor.

## Prerequisite is to install the Service Catalog

### By default, the template service broker shows objects that are globally available from the openshift project. It can also be configured to watch any other project that a cluster administrator chooses.


### Create ServiceCatalogAPIServer (YOU DO NOT NEED THIS IF YOU HAVE ALREADY INSTALLED THE SERVICECATALOG)

`oc create -f ServiceCatalogAPIServer.yaml`

### Create ServiceCatalogControllerManager (YOU DO NOT NEED THIS IF YOU HAVE ALREADY INSTALLED THE SERVICECATALOG)

`oc create -f ServiceCatalogControllerManager.yaml `

### Create Subscription for the TemplateServiceBroker
`oc create -f subcription-templateservicebroker.yaml -n openshift`

### Create the TemplateServiceBroker
`oc create -f templateservicebroker-template-service-broker.yaml -n openshift`

### Next, you must start the template service broker in order to access the template applications it provides. 

You will find your installed "Template Service Broker Operator" under "Installed Operators" under Catalog.

### Create the TemplateServiceBroker
`oc create -f templateservicebroker-template-service-broker.yaml -n openshift`

### Check 

Template service broker Pod status

From the Workloads → Pods page for the template-service-broker project, verify that the Pod that starts with apiserver- has a status of Running and readiness of Ready.

Cluster service broker status

From the Catalog → Broker Management → Service Brokers page, verify that the template-service-broker service broker has a status of Ready.

Service catalog controller manager Pod logs

From the Workloads → Pods page for the openshift-service-catalog-controller-manager project, review the logs for each of the Pods and verify that you see a log entry with the message Successfully fetched catalog entries from broker.