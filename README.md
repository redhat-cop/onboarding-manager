# OpenShift Sandbox Project Manager

Creates sandbox projects for users.

Deploying the operator can be done by running:

    oc new-project sandbox-manager
    oc apply -f deploy/

Building the operator is also very simple.

    operator-sdk build quay.io/etsauer/sandbox-manager
