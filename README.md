# OpenShift Onboarding Manager

OpenShift Onboarding Manager is an operator for OpenShift that provides an automated workflow for project creation in OpenShift.

In most real world use cases, its difficult for administrators to allow developers the ability to simply create their own projects or namespaces, while still being able to support multiple teams with various needs and various skillset levels. This operator provides more advanced workflows that allow cluster administrators to maintain order in their namespace sprawl while still allowing them to provide self service project creation to developers.

## Features

- [Personal Sandboxes for all Users](#personal-sandboxes-for-all-users)

### Personal Sanboxes for all Users

When a user logs in to OpenShift, Onboarding Manager creates a sandbox project for that user to use. This feature keys off of the `User` resource in OpenShift.

    $ oc whoami
    esauer
    $ oc get users
    NAME         UID                                    FULL NAME            IDENTITIES
    ...
    esauer       c5256c56-a3cd-11e9-a5af-fa163ef11dde   Eric Sauer           paas_ldap_provider:uid=esauer,cn=users,cn=accounts,dc=example,dc=com
    ...
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
