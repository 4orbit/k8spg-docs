# Percona Operator for PostgreSQL 2.1.0 (Tech preview)

* **Date**

    May 4, 2023

* **Installation**

    [Installing Percona Operator for PostgreSQL](https://www.percona.com/doc/kubernetes-operator-for-postgresql/2.0/index.html#installation-guide) 


The Percona Operator is based on best practices for configuration and setup of
a [Percona Distribution for PostgreSQL on Kubernetes](https://www.percona.com/doc/postgresql/LATEST/index.html).
The benefits of the Operator are many, but saving time and delivering a
consistent and vetted environment is key.

!!! note

    Version 2.1.0 of the Percona Operator for PostgreSQL is a **tech preview release** and it is **not recommended for production environments.**
    As of today, we recommend using [Percona Operator for PostgreSQL 1.x](https://www.percona.com/https://docs.percona.com/percona-operator-for-postgresql/index.html), which is production-ready and contains everything you need to quickly and consistently deploy and scale PostgreSQL clusters in a Kubernetes-based environment, on-premises or in the cloud.

The *Percona Operator for PostgreSQL 2.x* is based on the 5.x branch of the [Postgres Operator developed by Crunchy Data](https://access.crunchydata.com/documentation/postgres-operator/latest/). Please see the main changes in this version below.

## Release Highlights

* Now it is [possible](../backups.md#restore) to restore previously saved backups not only to an already-esixting cluster, but also to some new Kubernetes-based environment

* Handy `pg`, `pg-backup`, and `pg-restore` short names have been added for the Operator Custom Resources, useful to quickly query the cluster state with the `kubectl get` command

## New Features

* {{ k8spgjira(158) }}: A possibility to [restore backups to a new Kubernetes-based environment](../backups.md#restore) with no existing Percona PostgreSQL Operator Custom Resource

* {{ k8spgjira(328) }}: The new `delete-pvc` finalizer allows to either delete or preserve Persistent Volumes at Custom Resource deletion

* {{ k8spgjira(330) }}: The new `delete-ssl` finalizer can now be used to automatically delete objects created for SSL (Secret, certificate, and issuer) in case of cluster deletion

* {{ k8spgjira(331) }}: Starting from now, the operator adds short names to its custom resources: `pg`, `pg-backup`, and `pg-restore`

## Improvements

* {{ k8spgjira(282) }}: PostgreSQL 15 is now officially supported by the Operator

* {{ k8spgjira(262) }}: Operator should not try to start PMM if there is no 'pmmserverkey or pmmserver' key in secret

* {{ k8spgjira(272) }}: pmm agent is not deleted from server inventory on pod termination

* {{ k8spgjira(278) }}: Keep finalizers consistent between cluster objects

* {{ k8spgjira(285) }}: More questions answered with telemetry

* {{ k8spgjira(295) }}: PerconaPGCluster CR status inconsistencies with other operators

* {{ k8spgjira(304) }}: Reconsider using trust in pg_hba.conf

* {{ k8spgjira(305) }}: Research migration process

* {{ k8spgjira(306) }}: Ensure feature parity with v1

* {{ k8spgjira(325) }}: Custom resource pause and shutdown alignment	Dmitriy Kostiuk	In Doc	Under Review	

* {{ k8spgjira(327) }}: Consider removing Crunchy status from PostgresClusterStatus

## Bugs Fixed

* {{ k8spgjira(217) }}: Point In Time recovery after a failover results in just 2 node cluster

* {{ k8spgjira(279) }}: Operator will crash after creating backup if there is no manual section in CR

* {{ k8spgjira(298) }}: Can't restart or pause the cluster

* {{ k8spgjira(309) }}: Can't customize the user secrets name

* {{ k8spgjira(321) }}: Update CR template

* {{ k8spgjira(321) }}: Invalid URL

* {{ k8spgjira(334) }}: monitoring user should not have some special characters in it's password

## Supported platforms

The following platforms were tested and are officially supported by the Operator
2.1.0:


* [Google Kubernetes Engine (GKE)](https://cloud.google.com/kubernetes-engine) 1.21 - 1.24

* [Amazon Elastic Container Service for Kubernetes (EKS)](https://aws.amazon.com) 1.20 - 1.22

* [OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift) 4.7 - 4.10

This list only includes the platforms that the Percona Operators are specifically tested on as part of the release process. Other Kubernetes flavors and versions depend on the backward compatibility offered by Kubernetes itself.

