# eapbinary
EAP binary deploy to openshift 3.11

```
oc new-project binary
oc import-image eap72-openshift --from=registry.access.redhat.com/jboss-eap-7/eap72-openshift --confirm
oc new-build --image-stream=eap72-openshift --name=myapp --binary=true
oc start-build myapp --from-file=aero.war
```
Wait for the build to complete. You can watch the logs by running the following:
```
oc logs bc/myapp -f
```
Once the build completes, an imagestream will get created which can be
used to create a deployment.

```
oc new-app --image-stream=myapp
```
Expose the service via a route
```
oc expose svc/myapp
```
Get the route and visit the app.
```
oc get routes
```

The ```--from-file=``` arg can also be a url.

