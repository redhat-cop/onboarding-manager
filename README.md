# OpenShift Onboarding Manager

OpenShift Onboarding Manager is an operator for OpenShift that provides an automated workflow for project creation in OpenShift.

In most real world use cases, its difficult for administrators to allow developers the ability to simply create their own projects or namespaces, while still being able to support multiple teams with various needs and various skillset levels. This operator provides more advanced workflows that allow cluster administrators to maintain order in their namespace sprawl while still allowing them to provide self service project creation to developers.

## Features

- Personal Sandboxes for all Users

### Personal Sanboxes for all Users

When a user logs in to OpenShift, Onboarding Manager creates a sandbox project for that user to use.

    $ oc whoami
    esauer
    $ oc get projects
    $ oc projects
    You have access to the following projects and can switch between them with 'oc project <projectname>':

    esauer-sbx

If the project is deleted, Onboarding Manager will automatically recreate it.

    $ oc delete project esauer-sbx
    $ oc projects
    You have access to the following projects and can switch between them with 'oc project <projectname>':

    esauer-sbx

## Deployment

Creates sandbox projects for users.

Deploying the operator can be done by running:

    oc new-project sandbox-manager
    oc apply -f deploy/

## Building

Building the operator is also very simple.

    operator-sdk build quay.io/etsauer/sandbox-manager
