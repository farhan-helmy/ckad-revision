# CKAD Revision 

1. Kena study helm sebab helm masuk
- example question

---
Task weight: 5%

Team Mercury asked you to perform some operations using Helm, all in Namespace mercury:

- Delete release internal-issue-report-apiv1
- Upgrade release internal-issue-report-apiv2 to any newer version of chart bitnami/nginx available
- Install a new release internal-issue-report-apache of chart bitnami/apache. The Deployment should have two replicas, set these via Helm-values during install
- There seems to be a broken release, stuck in pending-install state. Find it and delete it
---

## Mount volume is like this
```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx
  name: nginx
spec:
  volumes: # add a volumes list
  - name: myvolume # just a name, you'll reference this in the pods
    configMap:
      name: cmvolume # name of your configmap
  containers:
  - image: nginx
    imagePullPolicy: IfNotPresent
    name: nginx
    resources: {}
    volumeMounts: # your volume mounts are listed here
    - name: myvolume # the name that you specified in pod.spec.volumes.name
      mountPath: /etc/lala # the path inside your container
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}
```
