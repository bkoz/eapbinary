# eapbinary
EAP binary deploy to openshift 3.11

```
oc new-build --image-stream=jboss-eap71-openshift --name=myapp --binary=true
oc import-image eap72-openshift --from=registry.access.redhat.com/jboss-eap-7/eap72-openshift --confirm
oc new-build --image-stream=eap72-openshift --name=myapp --binary=true
oc start-build myapp --from-file=aero.war
oc new-app myapp
oc expose svc/myapp
```
The ```--from-file=``` can also be a url.

