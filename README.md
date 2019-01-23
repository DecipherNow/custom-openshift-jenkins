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



## Resources

This repo is based heavily from https://github.com/siamaksade/jenkins-blueocean and the corresponding YouTube video: https://www.youtube.com/watch?v=IQ8H7XNbQ-8

https://github.com/Cingulara/custom-jenkins-openshift
