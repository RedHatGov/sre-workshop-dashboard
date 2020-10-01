# OpenShift Site Reliability Engineering Workshop

This repo contains the lab guides for a workshop on OpenShift SRE. These labs have been designed to work within an OpenShift Homeroom deployment.

## Deploying this workshop
Assuming you have a cluster and that you are logged with admin privileges.

1. Set a local `CLUSTER_SUBDOMAIN` environment variable
    > `CLUSTER_SUBDOMAIN=<apps.openshift.com>`

2. Create a project for the homeroom to live
    > `oc new-project homeroom --display-name="Homeroom Workshops"`

3. Grab the template to deploy a `workshop-spawner`. Note the `WORKSHOP_IMAGE` tag should be changed with the corresponding release you want to deploy.
> ```
> oc process -f https://raw.githubusercontent.com/RedHatGov/workshop-spawner/develop/templates/hosted-workshop-production.json \
>    -p SPAWNER_NAMESPACE=homeroom \
>    -p CLUSTER_SUBDOMAIN=$CLUSTER_SUBDOMAIN \
>    -p WORKSHOP_NAME=sre-workshop \
>    -p CONSOLE_IMAGE=quay.io/openshift/origin-console:4.5 \
>    -p WORKSHOP_IMAGE=quay.io/redhatgov/sre-workshop-dashboard:0.0.1 \
>    | oc apply -n homeroom -f -
> ```

## Access info for the workshop
Your workshop attendees will need user accounts in the OpenShift cluster.

Now give this URL (or preferably a shortened version) to your workshop attendees:
>`echo https://sre-workshop-homeroom.$CLUSTER_SUBDOMAIN`

## Cleaning up after the workshop
As long as no one else is running a homeroom workshop in the same cluster, you can clean up with the following:
>`oc delete project homeroom`