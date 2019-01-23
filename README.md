# Custom Jenkins Build for OpenShift

This repository is meant to be used with Jenkins S2I on OpenShift to install and enable Blue Ocean plugin on the official Jenkins image provided in OpenShift.

## Create the Jenkins Project in OpenShift

```bash
oc new-project jenkins
```

## Create the Custom Jenkins S2I build

Run this command in the `Jenkins` project

```bash
oc new-build jenkins:2~https://github.com/deciphernow/custom-openshift-jenkins.git --name=custom-jenkins
```

This command creates a new ImageStream and BuildConfig for the custom Jenkins image.

## Deploy Jenkins with the new Image

This command increases the Memory Limit from the default of 512M to 2G; uses the jenkins namespace and our new custom-jenkins image

```bash
oc process -p MEMORY_LIMIT=2Gi -p NAMESPACE=jenkins -p JENKINS_IMAGE_STREAM_TAG=custom-jenkins:latest -n openshift jenkins-ephemeral | oc apply -f-
```

## Resources

This repo is based heavily from https://github.com/siamaksade/jenkins-blueocean and the corresponding YouTube video: https://www.youtube.com/watch?v=IQ8H7XNbQ-8
