# Labels


```yaml
apiVersion: v1
kind: Pod
metadata:
  name: helloworld
  labels:
    env: production
    author: baz
    application_type: ui
    release-version: "1.0"
spec:
  containers:
  - name: helloworld
    image: helloworld

```

To update the value of a label, use the `--overwrite` flag in the command as follows: `kubectl label po/helloworld app=helloworldapp --overwrite` 


You can search for labels with the flag `--selector` (or `-l`). If you want to search for all the pods that are running in production, you can run `kubectl get pods --selector env=production` as shown below:

`kubectl get pods --selector env=production`

You can also do more complicated searches, like finding any pods owned by Karthik in the development tier, by the following query `dev-lead=karthik,env=staging`:

`kubectl get pods -l dev-lead!=karthik,env=production`


The opposite of "in" is "notin". Surprise. "Notin" is supported as well, as shown in this example:

`kubectl get pods -l 'release-version notin (1.0,2.0)'`

```
```

Finally, sometimes your label might not have a value assigned to it, but you can still search by label name.

`kubectl get pods -l 'release-version'`  




