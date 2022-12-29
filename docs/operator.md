---
title: Percona PostgreSQL Operator Custom Resource Options
draft: false
weight: 1
description: Custom Resource Options
---

Packages:

- [pg.percona.com/v2beta1](#pgperconacomv2beta1)

<h1 id="pgperconacomv2beta1">pg.percona.com/v2beta1</h1>

Resource Types:

- [PerconaPGCluster](#perconapgcluster)

- [PerconaPGBackup](#perconapgbackup)

- [PerconaPGRestore](#perconapgrestore)




<h2 id="perconapgcluster">PerconaPGCluster</h2>






PerconaPGCluster is the CRD that defines a Percona PG Cluster

|                 | |
|-----------------|-|
| **Key**         | spec |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | status |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterspec">
  PerconaPGCluster.spec
  <sup><sup><a href="#perconapgcluster">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | backups |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | PostgreSQL backup configuration |
| | |
| **Key**         | instances |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Specifies one or more sets of PostgreSQL pods that replicate data for this cluster. |
| | |
| **Key**         | postgresVersion |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | The major version of PostgreSQL installed in the PostgreSQL image |
| | |
| **Key**         | dataSource |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies a data source for bootstrapping the PostgreSQL cluster. |
| | |
| **Key**         | databaseInitSQL |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | DatabaseInitSQL defines a ConfigMap containing custom SQL that will be run after the cluster is initialized. This ConfigMap must be in the same namespace as the cluster. |
| | |
| **Key**         | expose |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Specification of the service that exposes the PostgreSQL primary instance. |
| | |
| **Key**         | image |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The image name to use for PostgreSQL containers. When omitted, the value comes from an operator environment variable. For standard PostgreSQL images, the format is RELATED_IMAGE_POSTGRES_{postgresVersion}, e.g. RELATED_IMAGE_POSTGRES_13. For PostGIS enabled PostgreSQL images, the format is RELATED_IMAGE_POSTGRES_{postgresVersion}_GIS_{postGISVersion}, e.g. RELATED_IMAGE_POSTGRES_13_GIS_3.1. |
| | |
| **Key**         | imagePullPolicy |
| **Value**       | enum |
| **Required**    | false |
| **Example**     | |
| **Description** | ImagePullPolicy is used to determine when Kubernetes will attempt to pull (download) container images. More info: https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy |
| | |
| **Key**         | imagePullSecrets |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The image pull secrets used to pull from a private registry Changing this value causes all running pods to restart. https://k8s.io/docs/tasks/configure-pod-container/pull-image-private-registry/ |
| | |
| **Key**         | openshift |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether or not the PostgreSQL cluster is being deployed to an OpenShift environment. If the field is unset, the operator will automatically detect the environment. |
| | |
| **Key**         | patroni |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | paused |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Suspends the rollout and reconciliation of changes made to the PostgresCluster spec. |
| | |
| **Key**         | pmm |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The specification of PMM sidecars. |
| | |
| **Key**         | port |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The port on which PostgreSQL should listen. |
| | |
| **Key**         | proxy |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The specification of a proxy that connects to PostgreSQL. |
| | |
| **Key**         | secrets |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | shutdown |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether or not the PostgreSQL cluster should be stopped. When this is true, workloads are scaled to zero and CronJobs are suspended. Other resources, such as Services and Volumes, remain in place. |
| | |
| **Key**         | standby |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Run this cluster as a read-only copy of an existing cluster or archive. |
| | |
| **Key**         | users |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Users to create inside PostgreSQL and the databases they should access. The default creates one user that can access one database matching the PostgresCluster name. An empty list creates no users. Removing a user from this list does NOT drop the user nor revoke their access. |
| | |



<h3 id="perconapgclusterspecbackups">
  PerconaPGCluster.spec.backups
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



PostgreSQL backup configuration

|                 | |
|-----------------|-|
| **Key**         | pgbackrest |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | pgBackRest archive configuration |
| | |



<h3 id="perconapgclusterspecbackupspgbackrest">
  PerconaPGCluster.spec.backups.pgbackrest
  <sup><sup><a href="#perconapgclusterspecbackups">↩ Parent</a></sup></sup>
</h3>



pgBackRest archive configuration

|                 | |
|-----------------|-|
| **Key**         | repos |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Defines a pgBackRest repository |
| | |
| **Key**         | configuration |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Projected volumes containing custom pgBackRest configuration.  These files are mounted under "/etc/pgbackrest/conf.d" alongside any pgBackRest configuration generated by the PostgreSQL Operator: https://pgbackrest.org/configuration.html |
| | |
| **Key**         | global |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | Global pgBackRest configuration settings.  These settings are included in the "global" section of the pgBackRest configuration generated by the PostgreSQL Operator, and then mounted under "/etc/pgbackrest/conf.d": https://pgbackrest.org/configuration.html |
| | |
| **Key**         | image |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The image name to use for pgBackRest containers.  Utilized to run pgBackRest repository hosts and backups. The image may also be set using the RELATED_IMAGE_PGBACKREST environment variable |
| | |
| **Key**         | jobs |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Jobs field allows configuration for all backup jobs |
| | |
| **Key**         | manual |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines details for manual pgBackRest backup Jobs |
| | |
| **Key**         | metadata |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Metadata contains metadata for PostgresCluster resources |
| | |
| **Key**         | repoHost |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines configuration for a pgBackRest dedicated repository host.  This section is only applicable if at least one "volume" (i.e. PVC-based) repository is defined in the "repos" section, therefore enabling a dedicated repository host Deployment. |
| | |
| **Key**         | restore |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines details for performing an in-place restore using pgBackRest |
| | |
| **Key**         | sidecars |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Configuration for pgBackRest sidecar containers |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindex">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



PGBackRestRepo represents a pgBackRest repository.  Only one of its members may be specified.

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the the repository |
| | |
| **Key**         | azure |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents a pgBackRest repository that is created using Azure storage |
| | |
| **Key**         | gcs |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents a pgBackRest repository that is created using Google Cloud Storage |
| | |
| **Key**         | s3 |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | RepoS3 represents a pgBackRest repository that is created using AWS S3 (or S3-compatible) storage |
| | |
| **Key**         | schedules |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the schedules for the pgBackRest backups Full, Differential and Incremental backup types are supported: https://pgbackrest.org/user-guide.html#concept/backup |
| | |
| **Key**         | volume |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents a pgBackRest repository that is created using a PersistentVolumeClaim |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexazure">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].azure
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindex">↩ Parent</a></sup></sup>
</h3>



Represents a pgBackRest repository that is created using Azure storage

|                 | |
|-----------------|-|
| **Key**         | container |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The Azure container utilized for the repository |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexgcs">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].gcs
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindex">↩ Parent</a></sup></sup>
</h3>



Represents a pgBackRest repository that is created using Google Cloud Storage

|                 | |
|-----------------|-|
| **Key**         | bucket |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The GCS bucket utilized for the repository |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexs3">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].s3
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindex">↩ Parent</a></sup></sup>
</h3>



RepoS3 represents a pgBackRest repository that is created using AWS S3 (or S3-compatible) storage

|                 | |
|-----------------|-|
| **Key**         | bucket |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The S3 bucket utilized for the repository |
| | |
| **Key**         | endpoint |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | A valid endpoint corresponding to the specified region |
| | |
| **Key**         | region |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The region corresponding to the S3 bucket |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexschedules">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].schedules
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindex">↩ Parent</a></sup></sup>
</h3>



Defines the schedules for the pgBackRest backups Full, Differential and Incremental backup types are supported: https://pgbackrest.org/user-guide.html#concept/backup

|                 | |
|-----------------|-|
| **Key**         | differential |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the Cron schedule for a differential pgBackRest backup. Follows the standard Cron schedule syntax: https://k8s.io/docs/concepts/workloads/controllers/cron-jobs/#cron-schedule-syntax |
| | |
| **Key**         | full |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the Cron schedule for a full pgBackRest backup. Follows the standard Cron schedule syntax: https://k8s.io/docs/concepts/workloads/controllers/cron-jobs/#cron-schedule-syntax |
| | |
| **Key**         | incremental |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the Cron schedule for an incremental pgBackRest backup. Follows the standard Cron schedule syntax: https://k8s.io/docs/concepts/workloads/controllers/cron-jobs/#cron-schedule-syntax |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolume">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindex">↩ Parent</a></sup></sup>
</h3>



Represents a pgBackRest repository that is created using a PersistentVolumeClaim

|                 | |
|-----------------|-|
| **Key**         | volumeClaimSpec |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Defines a PersistentVolumeClaim spec used to create and/or bind a volume |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspec">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume.volumeClaimSpec
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindexvolume">↩ Parent</a></sup></sup>
</h3>



Defines a PersistentVolumeClaim spec used to create and/or bind a volume

|                 | |
|-----------------|-|
| **Key**         | accessModes |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | accessModes contains the desired access modes the volume should have. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#access-modes-1 |
| | |
| **Key**         | dataSource |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field. |
| | |
| **Key**         | dataSourceRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled. |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources |
| | |
| **Key**         | selector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | selector is a label query over volumes to consider for binding. |
| | |
| **Key**         | storageClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | storageClassName is the name of the StorageClass required by the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#class-1 |
| | |
| **Key**         | volumeMode |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeMode defines what type of volume is required by the claim. Value of Filesystem is implied when not included in claim spec. |
| | |
| **Key**         | volumeName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeName is the binding reference to the PersistentVolume backing this claim. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspecdatasource">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume.volumeClaimSpec.dataSource
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspecdatasourceref">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume.volumeClaimSpec.dataSourceRef
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspecresources">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume.volumeClaimSpec.resources
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspecselector">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume.volumeClaimSpec.selector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



selector is a label query over volumes to consider for binding.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspecselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repos[index].volume.volumeClaimSpec.selector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestreposindexvolumevolumeclaimspecselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindex">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Projection that may be projected along with other supported volume types

|                 | |
|-----------------|-|
| **Key**         | configMap |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | configMap information about the configMap data to project |
| | |
| **Key**         | downwardAPI |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | downwardAPI information about the downwardAPI data to project |
| | |
| **Key**         | secret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | secret information about the secret data to project |
| | |
| **Key**         | serviceAccountToken |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | serviceAccountToken is information about the serviceAccountToken data to project |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexconfigmap">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].configMap
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



configMap information about the configMap data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced ConfigMap will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the ConfigMap, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional specify whether the ConfigMap or its keys must be defined |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexconfigmapitemsindex">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].configMap.items[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindexconfigmap">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapi">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].downwardAPI
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



downwardAPI information about the downwardAPI data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Items is a list of DownwardAPIVolume file |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapiitemsindex">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].downwardAPI.items[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapi">↩ Parent</a></sup></sup>
</h3>



DownwardAPIVolumeFile represents information to create the file containing the pod field

|                 | |
|-----------------|-|
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: Path is  the relative path name of the file to be created. Must not be absolute or contain the '..' path. Must be utf-8 encoded. The first item of the relative path must not start with '..' |
| | |
| **Key**         | fieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Required: Selects a field of the pod: only annotations, labels, name and namespace are supported. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: mode bits used to set permissions on this file, must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |
| **Key**         | resourceFieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapiitemsindexfieldref">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].downwardAPI.items[index].fieldRef
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapiitemsindex">↩ Parent</a></sup></sup>
</h3>



Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.

|                 | |
|-----------------|-|
| **Key**         | fieldPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path of the field to select in the specified API version. |
| | |
| **Key**         | apiVersion |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Version of the schema the FieldPath is written in terms of, defaults to "v1". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapiitemsindexresourcefieldref">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].downwardAPI.items[index].resourceFieldRef
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindexdownwardapiitemsindex">↩ Parent</a></sup></sup>
</h3>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.

|                 | |
|-----------------|-|
| **Key**         | resource |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: resource to select |
| | |
| **Key**         | containerName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container name: required for volumes, optional for env vars |
| | |
| **Key**         | divisor |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies the output format of the exposed resources, defaults to "1" |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexsecret">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].secret
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



secret information about the secret data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexsecretitemsindex">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].secret.items[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindexsecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestconfigurationindexserviceaccounttoken">
  PerconaPGCluster.spec.backups.pgbackrest.configuration[index].serviceAccountToken
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



serviceAccountToken is information about the serviceAccountToken data to project

|                 | |
|-----------------|-|
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the path relative to the mount point of the file to project the token into. |
| | |
| **Key**         | audience |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | audience is the intended audience of the token. A recipient of a token must identify itself with an identifier specified in the audience of the token, and otherwise should reject the token. The audience defaults to the identifier of the apiserver. |
| | |
| **Key**         | expirationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | expirationSeconds is the requested duration of validity of the service account token. As the token approaches expiration, the kubelet volume plugin will proactively rotate the service account token. The kubelet will start trying to rotate the token if the token is older than 80 percent of its time to live or if the token is older than 24 hours.Defaults to 1 hour and must be at least 10 minutes. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobs">
  PerconaPGCluster.spec.backups.pgbackrest.jobs
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Jobs field allows configuration for all backup jobs

|                 | |
|-----------------|-|
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of pgBackRest backup Job pods. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the pgBackRest backup Job pods. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource limits for backup jobs. Includes manual, scheduled and replica create backups |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of pgBackRest backup Job pods. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobs">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of pgBackRest backup Job pods. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobsaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobsresources">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.resources
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobs">↩ Parent</a></sup></sup>
</h3>



Resource limits for backup jobs. Includes manual, scheduled and replica create backups

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestjobstolerationsindex">
  PerconaPGCluster.spec.backups.pgbackrest.jobs.tolerations[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestjobs">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestmanual">
  PerconaPGCluster.spec.backups.pgbackrest.manual
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Defines details for manual pgBackRest backup Jobs

|                 | |
|-----------------|-|
| **Key**         | repoName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the pgBackRest repo to run the backup command against. |
| | |
| **Key**         | options |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command line options to include when running the pgBackRest backup command. https://pgbackrest.org/command.html#command-backup |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestmetadata">
  PerconaPGCluster.spec.backups.pgbackrest.metadata
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Metadata contains metadata for PostgresCluster resources

|                 | |
|-----------------|-|
| **Key**         | annotations |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | labels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohost">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Defines configuration for a pgBackRest dedicated repository host.  This section is only applicable if at least one "volume" (i.e. PVC-based) repository is defined in the "repos" section, therefore enabling a dedicated repository host Deployment.

|                 | |
|-----------------|-|
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of the Dedicated repo host pod. Changing this value causes repo host to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the pgBackRest repo host pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource requirements for a pgBackRest repository host |
| | |
| **Key**         | sshConfigMap |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | ConfigMap containing custom SSH configuration. Deprecated: Repository hosts use mTLS for encryption, authentication, and authorization. |
| | |
| **Key**         | sshSecret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Secret containing custom SSH keys. Deprecated: Repository hosts use mTLS for encryption, authentication, and authorization. |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of a PgBackRest repo host pod. Changing this value causes a restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |
| **Key**         | topologySpreadConstraints |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Topology spread constraints of a Dedicated repo host pod. Changing this value causes the repo host to restart. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/ |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohost">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of the Dedicated repo host pod. Changing this value causes repo host to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostresources">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.resources
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohost">↩ Parent</a></sup></sup>
</h3>



Resource requirements for a pgBackRest repository host

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostsshconfigmap">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.sshConfigMap
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohost">↩ Parent</a></sup></sup>
</h3>



ConfigMap containing custom SSH configuration. Deprecated: Repository hosts use mTLS for encryption, authentication, and authorization.

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced ConfigMap will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the ConfigMap, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional specify whether the ConfigMap or its keys must be defined |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostsshconfigmapitemsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.sshConfigMap.items[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostsshconfigmap">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostsshsecret">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.sshSecret
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohost">↩ Parent</a></sup></sup>
</h3>



Secret containing custom SSH keys. Deprecated: Repository hosts use mTLS for encryption, authentication, and authorization.

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohostsshsecretitemsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.sshSecret.items[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohostsshsecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohosttolerationsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.tolerations[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohost">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohosttopologyspreadconstraintsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.topologySpreadConstraints[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohost">↩ Parent</a></sup></sup>
</h3>



TopologySpreadConstraint specifies how to spread matching pods among the given topology.

|                 | |
|-----------------|-|
| **Key**         | maxSkew |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | MaxSkew describes the degree to which pods may be unevenly distributed. When `whenUnsatisfiable=DoNotSchedule`, it is the maximum permitted difference between the number of matching pods in the target topology and the global minimum. The global minimum is the minimum number of matching pods in an eligible domain or zero if the number of eligible domains is less than MinDomains. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 2/2/1: In this case, the global minimum is 1. | zone1 | zone2 | zone3 | |  P P  |  P P  |   P   | - if MaxSkew is 1, incoming pod can only be scheduled to zone3 to become 2/2/2; scheduling it onto zone1(zone2) would make the ActualSkew(3-1) on zone1(zone2) violate MaxSkew(1). - if MaxSkew is 2, incoming pod can be scheduled onto any zone. When `whenUnsatisfiable=ScheduleAnyway`, it is used to give higher precedence to topologies that satisfy it. It's a required field. Default value is 1 and 0 is not allowed. |
| | |
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | TopologyKey is the key of node labels. Nodes that have a label with this key and identical values are considered to be in the same topology. We consider each <key, value> as a "bucket", and try to put balanced number of pods into each bucket. We define a domain as a particular instance of a topology. Also, we define an eligible domain as a domain whose nodes meet the requirements of nodeAffinityPolicy and nodeTaintsPolicy. e.g. If TopologyKey is "kubernetes.io/hostname", each Node is a domain of that topology. And, if TopologyKey is "topology.kubernetes.io/zone", each zone is a domain of that topology. It's a required field. |
| | |
| **Key**         | whenUnsatisfiable |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | WhenUnsatisfiable indicates how to deal with a pod if it doesn't satisfy the spread constraint. - DoNotSchedule (default) tells the scheduler not to schedule it. - ScheduleAnyway tells the scheduler to schedule the pod in any location, but giving higher precedence to topologies that would help reduce the skew. A constraint is considered "Unsatisfiable" for an incoming pod if and only if every possible node assignment for that pod would violate "MaxSkew" on some topology. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 3/1/1: | zone1 | zone2 | zone3 | | P P P |   P   |   P   | If WhenUnsatisfiable is set to DoNotSchedule, incoming pod can only be scheduled to zone2(zone3) to become 3/2/1(3/1/2) as ActualSkew(2-1) on zone2(zone3) satisfies MaxSkew(1). In other words, the cluster can still be imbalanced, but scheduler won't make it *more* imbalanced. It's a required field. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain. |
| | |
| **Key**         | matchLabelKeys |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | MatchLabelKeys is a set of pod label keys to select the pods over which spreading will be calculated. The keys are used to lookup values from the incoming pod labels, those key-value labels are ANDed with labelSelector to select the group of existing pods over which spreading will be calculated for the incoming pod. Keys that don't exist in the incoming pod labels will be ignored. A null or empty list means only match against labelSelector. |
| | |
| **Key**         | minDomains |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | MinDomains indicates a minimum number of eligible domains. When the number of eligible domains with matching topology keys is less than minDomains, Pod Topology Spread treats "global minimum" as 0, and then the calculation of Skew is performed. And when the number of eligible domains with matching topology keys equals or greater than minDomains, this value has no effect on scheduling. As a result, when the number of eligible domains is less than minDomains, scheduler won't schedule more than maxSkew Pods to those domains. If value is nil, the constraint behaves as if MinDomains is equal to 1. Valid values are integers greater than 0. When value is not nil, WhenUnsatisfiable must be DoNotSchedule. 
 For example, in a 3-zone cluster, MaxSkew is set to 2, MinDomains is set to 5 and pods with the same labelSelector spread as 2/2/2: | zone1 | zone2 | zone3 | |  P P  |  P P  |  P P  | The number of domains is less than 5(MinDomains), so "global minimum" is treated as 0. In this situation, new pod with the same labelSelector cannot be scheduled, because computed skew will be 3(3 - 0) if new Pod is scheduled to any of the three zones, it will violate MaxSkew. 
 This is a beta field and requires the MinDomainsInPodTopologySpread feature gate to be enabled (enabled by default). |
| | |
| **Key**         | nodeAffinityPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | NodeAffinityPolicy indicates how we will treat Pod's nodeAffinity/nodeSelector when calculating pod topology spread skew. Options are: - Honor: only nodes matching nodeAffinity/nodeSelector are included in the calculations. - Ignore: nodeAffinity/nodeSelector are ignored. All nodes are included in the calculations. 
 If this value is nil, the behavior is equivalent to the Honor policy. This is a alpha-level feature enabled by the NodeInclusionPolicyInPodTopologySpread feature flag. |
| | |
| **Key**         | nodeTaintsPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | NodeTaintsPolicy indicates how we will treat node taints when calculating pod topology spread skew. Options are: - Honor: nodes without taints, along with tainted nodes for which the incoming pod has a toleration, are included. - Ignore: node taints are ignored. All nodes are included. 
 If this value is nil, the behavior is equivalent to the Ignore policy. This is a alpha-level feature enabled by the NodeInclusionPolicyInPodTopologySpread feature flag. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohosttopologyspreadconstraintsindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.topologySpreadConstraints[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohosttopologyspreadconstraintsindex">↩ Parent</a></sup></sup>
</h3>



LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrepohosttopologyspreadconstraintsindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.repoHost.topologySpreadConstraints[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrepohosttopologyspreadconstraintsindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestore">
  PerconaPGCluster.spec.backups.pgbackrest.restore
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Defines details for performing an in-place restore using pgBackRest

|                 | |
|-----------------|-|
| **Key**         | enabled |
| **Value**       | boolean |
| **Required**    | true |
| **Example**     | |
| **Description** | Whether or not in-place pgBackRest restores are enabled for this PostgresCluster. |
| | |
| **Key**         | repoName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the pgBackRest repo within the source PostgresCluster that contains the backups that should be utilized to perform a pgBackRest restore when initializing the data source for the new PostgresCluster. |
| | |
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | clusterName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The name of an existing PostgresCluster to use as the data source for the new PostgresCluster. Defaults to the name of the PostgresCluster being created if not provided. |
| | |
| **Key**         | clusterNamespace |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The namespace of the cluster specified as the data source using the clusterName field. Defaults to the namespace of the PostgresCluster being created if not provided. |
| | |
| **Key**         | options |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command line options to include when running the pgBackRest restore command. https://pgbackrest.org/command.html#command-restore |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the pgBackRest restore Job pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource requirements for the pgBackRest restore Job. |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestore">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinity">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestoreaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoreresources">
  PerconaPGCluster.spec.backups.pgbackrest.restore.resources
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestore">↩ Parent</a></sup></sup>
</h3>



Resource requirements for the pgBackRest restore Job.

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestrestoretolerationsindex">
  PerconaPGCluster.spec.backups.pgbackrest.restore.tolerations[index]
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestrestore">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestsidecars">
  PerconaPGCluster.spec.backups.pgbackrest.sidecars
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrest">↩ Parent</a></sup></sup>
</h3>



Configuration for pgBackRest sidecar containers

|                 | |
|-----------------|-|
| **Key**         | pgbackrest |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the configuration for the pgBackRest sidecar container |
| | |
| **Key**         | pgbackrestConfig |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the configuration for the pgBackRest config sidecar container |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestsidecarspgbackrest">
  PerconaPGCluster.spec.backups.pgbackrest.sidecars.pgbackrest
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestsidecars">↩ Parent</a></sup></sup>
</h3>



Defines the configuration for the pgBackRest sidecar container

|                 | |
|-----------------|-|
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource requirements for a sidecar container |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestsidecarspgbackrestresources">
  PerconaPGCluster.spec.backups.pgbackrest.sidecars.pgbackrest.resources
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestsidecarspgbackrest">↩ Parent</a></sup></sup>
</h3>



Resource requirements for a sidecar container

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestsidecarspgbackrestconfig">
  PerconaPGCluster.spec.backups.pgbackrest.sidecars.pgbackrestConfig
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestsidecars">↩ Parent</a></sup></sup>
</h3>



Defines the configuration for the pgBackRest config sidecar container

|                 | |
|-----------------|-|
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource requirements for a sidecar container |
| | |



<h3 id="perconapgclusterspecbackupspgbackrestsidecarspgbackrestconfigresources">
  PerconaPGCluster.spec.backups.pgbackrest.sidecars.pgbackrestConfig.resources
  <sup><sup><a href="#perconapgclusterspecbackupspgbackrestsidecarspgbackrestconfig">↩ Parent</a></sup></sup>
</h3>



Resource requirements for a sidecar container

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecinstancesindex">
  PerconaPGCluster.spec.instances[index]
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | dataVolumeClaimSpec |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Defines a PersistentVolumeClaim for PostgreSQL data. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes |
| | |
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of a PostgreSQL pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | metadata |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Metadata contains metadata for PostgresCluster resources |
| | |
| **Key**         | minAvailable |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum number of pods that should be available at a time. Defaults to one when the replicas field is greater than one. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name that associates this set of PostgreSQL pods. This field is optional when only one instance set is defined. Each instance set in a cluster must have a unique name. The combined length of this and the cluster name must be 46 characters or less. |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the PostgreSQL pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | replicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of desired PostgreSQL pods. |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Compute resources of a PostgreSQL container. |
| | |
| **Key**         | sidecars |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom sidecars for PostgreSQL instance pods. Changing this value causes PostgreSQL to restart. |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of a PostgreSQL pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |
| **Key**         | topologySpreadConstraints |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Topology spread constraints of a PostgreSQL pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/ |
| | |
| **Key**         | walVolumeClaimSpec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines a separate PersistentVolumeClaim for PostgreSQL's write-ahead log. More info: https://www.postgresql.org/docs/current/wal.html |
| | |



<h3 id="perconapgclusterspecinstancesindexdatavolumeclaimspec">
  PerconaPGCluster.spec.instances[index].dataVolumeClaimSpec
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



Defines a PersistentVolumeClaim for PostgreSQL data. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes

|                 | |
|-----------------|-|
| **Key**         | accessModes |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | accessModes contains the desired access modes the volume should have. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#access-modes-1 |
| | |
| **Key**         | dataSource |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field. |
| | |
| **Key**         | dataSourceRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled. |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources |
| | |
| **Key**         | selector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | selector is a label query over volumes to consider for binding. |
| | |
| **Key**         | storageClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | storageClassName is the name of the StorageClass required by the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#class-1 |
| | |
| **Key**         | volumeMode |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeMode defines what type of volume is required by the claim. Value of Filesystem is implied when not included in claim spec. |
| | |
| **Key**         | volumeName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeName is the binding reference to the PersistentVolume backing this claim. |
| | |



<h3 id="perconapgclusterspecinstancesindexdatavolumeclaimspecdatasource">
  PerconaPGCluster.spec.instances[index].dataVolumeClaimSpec.dataSource
  <sup><sup><a href="#perconapgclusterspecinstancesindexdatavolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecinstancesindexdatavolumeclaimspecdatasourceref">
  PerconaPGCluster.spec.instances[index].dataVolumeClaimSpec.dataSourceRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexdatavolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecinstancesindexdatavolumeclaimspecresources">
  PerconaPGCluster.spec.instances[index].dataVolumeClaimSpec.resources
  <sup><sup><a href="#perconapgclusterspecinstancesindexdatavolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecinstancesindexdatavolumeclaimspecselector">
  PerconaPGCluster.spec.instances[index].dataVolumeClaimSpec.selector
  <sup><sup><a href="#perconapgclusterspecinstancesindexdatavolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



selector is a label query over volumes to consider for binding.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexdatavolumeclaimspecselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].dataVolumeClaimSpec.selector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexdatavolumeclaimspecselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinity">
  PerconaPGCluster.spec.instances[index].affinity
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of a PostgreSQL pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinity">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.instances[index].affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinity">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinity">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexmetadata">
  PerconaPGCluster.spec.instances[index].metadata
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



Metadata contains metadata for PostgresCluster resources

|                 | |
|-----------------|-|
| **Key**         | annotations |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | labels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterspecinstancesindexresources">
  PerconaPGCluster.spec.instances[index].resources
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



Compute resources of a PostgreSQL container.

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindex">
  PerconaPGCluster.spec.instances[index].sidecars[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



A single application container that you want to run within a pod.

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name of the container specified as a DNS_LABEL. Each container in a pod must have a unique name (DNS_LABEL). Cannot be updated. |
| | |
| **Key**         | args |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Arguments to the entrypoint. The container image's CMD is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container's environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. "$$(VAR_NAME)" will produce the string literal "$(VAR_NAME)". Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell |
| | |
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Entrypoint array. Not executed within a shell. The container image's ENTRYPOINT is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container's environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. "$$(VAR_NAME)" will produce the string literal "$(VAR_NAME)". Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell |
| | |
| **Key**         | env |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | List of environment variables to set in the container. Cannot be updated. |
| | |
| **Key**         | envFrom |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | List of sources to populate environment variables in the container. The keys defined within a source must be a C_IDENTIFIER. All invalid keys will be reported as an event when the container is starting. When a key exists in multiple sources, the value associated with the last source will take precedence. Values defined by an Env with a duplicate key will take precedence. Cannot be updated. |
| | |
| **Key**         | image |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container image name. More info: https://kubernetes.io/docs/concepts/containers/images This field is optional to allow higher level config management to default or override container images in workload controllers like Deployments and StatefulSets. |
| | |
| **Key**         | imagePullPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Image pull policy. One of Always, Never, IfNotPresent. Defaults to Always if :latest tag is specified, or IfNotPresent otherwise. Cannot be updated. More info: https://kubernetes.io/docs/concepts/containers/images#updating-images |
| | |
| **Key**         | lifecycle |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Actions that the management system should take in response to container lifecycle events. Cannot be updated. |
| | |
| **Key**         | livenessProbe |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | ports |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | List of ports to expose from the container. Not specifying a port here DOES NOT prevent that port from being exposed. Any port which is listening on the default "0.0.0.0" address inside a container will be accessible from the network. Modifying this array with strategic merge patch may corrupt the data. For more information See https://github.com/kubernetes/kubernetes/issues/108255. Cannot be updated. |
| | |
| **Key**         | readinessProbe |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | securityContext |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/ |
| | |
| **Key**         | startupProbe |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod's lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | stdin |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container should allocate a buffer for stdin in the container runtime. If this is not set, reads from stdin in the container will always result in EOF. Default is false. |
| | |
| **Key**         | stdinOnce |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether the container runtime should close the stdin channel after it has been opened by a single attach. When stdin is true the stdin stream will remain open across multiple attach sessions. If stdinOnce is set to true, stdin is opened on container start, is empty until the first client attaches to stdin, and then remains open and accepts data until the client disconnects, at which time stdin is closed and remains closed until the container is restarted. If this flag is false, a container processes that reads from stdin will never receive an EOF. Default is false |
| | |
| **Key**         | terminationMessagePath |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Path at which the file to which the container's termination message will be written is mounted into the container's filesystem. Message written is intended to be brief final status, such as an assertion failure message. Will be truncated by the node if greater than 4096 bytes. The total message length across all containers will be limited to 12kb. Defaults to /dev/termination-log. Cannot be updated. |
| | |
| **Key**         | terminationMessagePolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Indicate how the termination message should be populated. File will use the contents of terminationMessagePath to populate the container status message on both success and failure. FallbackToLogsOnError will use the last chunk of container log output if the termination message file is empty and the container exited with an error. The log output is limited to 2048 bytes or 80 lines, whichever is smaller. Defaults to File. Cannot be updated. |
| | |
| **Key**         | tty |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container should allocate a TTY for itself, also requires 'stdin' to be true. Default is false. |
| | |
| **Key**         | volumeDevices |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeDevices is the list of block devices to be used by the container. |
| | |
| **Key**         | volumeMounts |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Pod volumes to mount into the container's filesystem. Cannot be updated. |
| | |
| **Key**         | workingDir |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container's working directory. If not specified, the container runtime's default will be used, which might be configured in the container image. Cannot be updated. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].env[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



EnvVar represents an environment variable present in a Container.

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name of the environment variable. Must be a C_IDENTIFIER. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Variable references $(VAR_NAME) are expanded using the previously defined environment variables in the container and any service environment variables. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. "$$(VAR_NAME)" will produce the string literal "$(VAR_NAME)". Escaped references will never be expanded, regardless of whether the variable exists or not. Defaults to "". |
| | |
| **Key**         | valueFrom |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Source for the environment variable's value. Cannot be used if value is not empty. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefrom">
  PerconaPGCluster.spec.instances[index].sidecars[index].env[index].valueFrom
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvindex">↩ Parent</a></sup></sup>
</h3>



Source for the environment variable's value. Cannot be used if value is not empty.

|                 | |
|-----------------|-|
| **Key**         | configMapKeyRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a key of a ConfigMap. |
| | |
| **Key**         | fieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels['<KEY>']`, `metadata.annotations['<KEY>']`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs. |
| | |
| **Key**         | resourceFieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported. |
| | |
| **Key**         | secretKeyRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a key of a secret in the pod's namespace |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefromconfigmapkeyref">
  PerconaPGCluster.spec.instances[index].sidecars[index].env[index].valueFrom.configMapKeyRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a key of a ConfigMap.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The key to select. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the ConfigMap or its key must be defined |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefromfieldref">
  PerconaPGCluster.spec.instances[index].sidecars[index].env[index].valueFrom.fieldRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels['<KEY>']`, `metadata.annotations['<KEY>']`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.

|                 | |
|-----------------|-|
| **Key**         | fieldPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path of the field to select in the specified API version. |
| | |
| **Key**         | apiVersion |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Version of the schema the FieldPath is written in terms of, defaults to "v1". |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefromresourcefieldref">
  PerconaPGCluster.spec.instances[index].sidecars[index].env[index].valueFrom.resourceFieldRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.

|                 | |
|-----------------|-|
| **Key**         | resource |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: resource to select |
| | |
| **Key**         | containerName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container name: required for volumes, optional for env vars |
| | |
| **Key**         | divisor |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies the output format of the exposed resources, defaults to "1" |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefromsecretkeyref">
  PerconaPGCluster.spec.instances[index].sidecars[index].env[index].valueFrom.secretKeyRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a key of a secret in the pod's namespace

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The key of the secret to select from.  Must be a valid secret key. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvfromindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].envFrom[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



EnvFromSource represents the source of a set of ConfigMaps

|                 | |
|-----------------|-|
| **Key**         | configMapRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The ConfigMap to select from |
| | |
| **Key**         | prefix |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | An optional identifier to prepend to each key in the ConfigMap. Must be a C_IDENTIFIER. |
| | |
| **Key**         | secretRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The Secret to select from |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvfromindexconfigmapref">
  PerconaPGCluster.spec.instances[index].sidecars[index].envFrom[index].configMapRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvfromindex">↩ Parent</a></sup></sup>
</h3>



The ConfigMap to select from

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the ConfigMap must be defined |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexenvfromindexsecretref">
  PerconaPGCluster.spec.instances[index].sidecars[index].envFrom[index].secretRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexenvfromindex">↩ Parent</a></sup></sup>
</h3>



The Secret to select from

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the Secret must be defined |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecycle">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



Actions that the management system should take in response to container lifecycle events. Cannot be updated.

|                 | |
|-----------------|-|
| **Key**         | postStart |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks |
| | |
| **Key**         | preStop |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod's termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod's termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststart">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.postStart
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecycle">↩ Parent</a></sup></sup>
</h3>



PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststartexec">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.postStart.exec
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststart">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststarthttpget">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.postStart.httpGet
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststart">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststarthttpgethttpheadersindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.postStart.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststarthttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststarttcpsocket">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.postStart.tcpSocket
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecyclepoststart">↩ Parent</a></sup></sup>
</h3>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecycleprestop">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.preStop
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecycle">↩ Parent</a></sup></sup>
</h3>



PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod's termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod's termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecycleprestopexec">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.preStop.exec
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecycleprestop">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecycleprestophttpget">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.preStop.httpGet
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecycleprestop">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecycleprestophttpgethttpheadersindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.preStop.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecycleprestophttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlifecycleprestoptcpsocket">
  PerconaPGCluster.spec.instances[index].sidecars[index].lifecycle.preStop.tcpSocket
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlifecycleprestop">↩ Parent</a></sup></sup>
</h3>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlivenessprobe">
  PerconaPGCluster.spec.instances[index].sidecars[index].livenessProbe
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | failureThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1. |
| | |
| **Key**         | grpc |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | initialDelaySeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | periodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1. |
| | |
| **Key**         | successThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | TCPSocket specifies an action involving a TCP port. |
| | |
| **Key**         | terminationGracePeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod's terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset. |
| | |
| **Key**         | timeoutSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlivenessprobeexec">
  PerconaPGCluster.spec.instances[index].sidecars[index].livenessProbe.exec
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlivenessprobegrpc">
  PerconaPGCluster.spec.instances[index].sidecars[index].livenessProbe.grpc
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Port number of the gRPC service. Number must be in the range 1 to 65535. |
| | |
| **Key**         | service |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlivenessprobehttpget">
  PerconaPGCluster.spec.instances[index].sidecars[index].livenessProbe.httpGet
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlivenessprobehttpgethttpheadersindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].livenessProbe.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlivenessprobehttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexlivenessprobetcpsocket">
  PerconaPGCluster.spec.instances[index].sidecars[index].livenessProbe.tcpSocket
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



TCPSocket specifies an action involving a TCP port.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexportsindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].ports[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



ContainerPort represents a network port in a single container.

|                 | |
|-----------------|-|
| **Key**         | containerPort |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Number of port to expose on the pod's IP address. This must be a valid port number, 0 < x < 65536. |
| | |
| **Key**         | hostIP |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | What host IP to bind the external port to. |
| | |
| **Key**         | hostPort |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of port to expose on the host. If specified, this must be a valid port number, 0 < x < 65536. If HostNetwork is specified, this must match ContainerPort. Most containers do not need this. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | If specified, this must be an IANA_SVC_NAME and unique within the pod. Each named port in a pod must have a unique name. Name for the port that can be referred to by services. |
| | |
| **Key**         | protocol |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Protocol for port. Must be UDP, TCP, or SCTP. Defaults to "TCP". |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexreadinessprobe">
  PerconaPGCluster.spec.instances[index].sidecars[index].readinessProbe
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | failureThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1. |
| | |
| **Key**         | grpc |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | initialDelaySeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | periodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1. |
| | |
| **Key**         | successThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | TCPSocket specifies an action involving a TCP port. |
| | |
| **Key**         | terminationGracePeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod's terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset. |
| | |
| **Key**         | timeoutSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexreadinessprobeexec">
  PerconaPGCluster.spec.instances[index].sidecars[index].readinessProbe.exec
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexreadinessprobegrpc">
  PerconaPGCluster.spec.instances[index].sidecars[index].readinessProbe.grpc
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Port number of the gRPC service. Number must be in the range 1 to 65535. |
| | |
| **Key**         | service |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexreadinessprobehttpget">
  PerconaPGCluster.spec.instances[index].sidecars[index].readinessProbe.httpGet
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexreadinessprobehttpgethttpheadersindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].readinessProbe.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexreadinessprobehttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexreadinessprobetcpsocket">
  PerconaPGCluster.spec.instances[index].sidecars[index].readinessProbe.tcpSocket
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



TCPSocket specifies an action involving a TCP port.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexresources">
  PerconaPGCluster.spec.instances[index].sidecars[index].resources
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexsecuritycontext">
  PerconaPGCluster.spec.instances[index].sidecars[index].securityContext
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/

|                 | |
|-----------------|-|
| **Key**         | allowPrivilegeEscalation |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | AllowPrivilegeEscalation controls whether a process can gain more privileges than its parent process. This bool directly controls if the no_new_privs flag will be set on the container process. AllowPrivilegeEscalation is true always when the container is: 1) run as Privileged 2) has CAP_SYS_ADMIN Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | capabilities |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | privileged |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Run container in privileged mode. Processes in privileged containers are essentially equivalent to root on the host. Defaults to false. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | procMount |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | procMount denotes the type of proc mount to use for the containers. The default is DefaultProcMount which uses the container runtime defaults for readonly paths and masked paths. This requires the ProcMountType feature flag to be enabled. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | readOnlyRootFilesystem |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container has a read-only root filesystem. Default is false. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | runAsGroup |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | runAsNonRoot |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. |
| | |
| **Key**         | runAsUser |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | seLinuxOptions |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | seccompProfile |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The seccomp options to use by this container. If seccomp options are provided at both the pod & container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | windowsOptions |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexsecuritycontextcapabilities">
  PerconaPGCluster.spec.instances[index].sidecars[index].securityContext.capabilities
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | add |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Added capabilities |
| | |
| **Key**         | drop |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Removed capabilities |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexsecuritycontextselinuxoptions">
  PerconaPGCluster.spec.instances[index].sidecars[index].securityContext.seLinuxOptions
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | level |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Level is SELinux level label that applies to the container. |
| | |
| **Key**         | role |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Role is a SELinux role label that applies to the container. |
| | |
| **Key**         | type |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Type is a SELinux type label that applies to the container. |
| | |
| **Key**         | user |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | User is a SELinux user label that applies to the container. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexsecuritycontextseccompprofile">
  PerconaPGCluster.spec.instances[index].sidecars[index].securityContext.seccompProfile
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The seccomp options to use by this container. If seccomp options are provided at both the pod & container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | type |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied. |
| | |
| **Key**         | localhostProfile |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet's configured seccomp profile location. Must only be set if type is "Localhost". |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexsecuritycontextwindowsoptions">
  PerconaPGCluster.spec.instances[index].sidecars[index].securityContext.windowsOptions
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.

|                 | |
|-----------------|-|
| **Key**         | gmsaCredentialSpec |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field. |
| | |
| **Key**         | gmsaCredentialSpecName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | GMSACredentialSpecName is the name of the GMSA credential spec to use. |
| | |
| **Key**         | hostProcess |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | HostProcess determines if a container should be run as a 'Host Process' container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod's containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true. |
| | |
| **Key**         | runAsUserName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexstartupprobe">
  PerconaPGCluster.spec.instances[index].sidecars[index].startupProbe
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod's lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | failureThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1. |
| | |
| **Key**         | grpc |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | initialDelaySeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | periodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1. |
| | |
| **Key**         | successThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | TCPSocket specifies an action involving a TCP port. |
| | |
| **Key**         | terminationGracePeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod's terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset. |
| | |
| **Key**         | timeoutSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexstartupprobeexec">
  PerconaPGCluster.spec.instances[index].sidecars[index].startupProbe.exec
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexstartupprobegrpc">
  PerconaPGCluster.spec.instances[index].sidecars[index].startupProbe.grpc
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Port number of the gRPC service. Number must be in the range 1 to 65535. |
| | |
| **Key**         | service |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexstartupprobehttpget">
  PerconaPGCluster.spec.instances[index].sidecars[index].startupProbe.httpGet
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexstartupprobehttpgethttpheadersindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].startupProbe.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexstartupprobehttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexstartupprobetcpsocket">
  PerconaPGCluster.spec.instances[index].sidecars[index].startupProbe.tcpSocket
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



TCPSocket specifies an action involving a TCP port.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexvolumedevicesindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].volumeDevices[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



volumeDevice describes a mapping of a raw block device within a container.

|                 | |
|-----------------|-|
| **Key**         | devicePath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | devicePath is the path inside of the container that the device will be mapped to. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | name must match the name of a persistentVolumeClaim in the pod |
| | |



<h3 id="perconapgclusterspecinstancesindexsidecarsindexvolumemountsindex">
  PerconaPGCluster.spec.instances[index].sidecars[index].volumeMounts[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexsidecarsindex">↩ Parent</a></sup></sup>
</h3>



VolumeMount describes a mounting of a Volume within a container.

|                 | |
|-----------------|-|
| **Key**         | mountPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path within the container at which the volume should be mounted.  Must not contain ':'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This must match the Name of a Volume. |
| | |
| **Key**         | mountPropagation |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | mountPropagation determines how mounts are propagated from the host to container and the other way around. When not set, MountPropagationNone is used. This field is beta in 1.10. |
| | |
| **Key**         | readOnly |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Mounted read-only if true, read-write otherwise (false or unspecified). Defaults to false. |
| | |
| **Key**         | subPath |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path within the volume from which the container's volume should be mounted. Defaults to "" (volume's root). |
| | |
| **Key**         | subPathExpr |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Expanded path within the volume from which the container's volume should be mounted. Behaves similarly to SubPath but environment variable references $(VAR_NAME) are expanded using the container's environment. Defaults to "" (volume's root). SubPathExpr and SubPath are mutually exclusive. |
| | |



<h3 id="perconapgclusterspecinstancesindextolerationsindex">
  PerconaPGCluster.spec.instances[index].tolerations[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecinstancesindextopologyspreadconstraintsindex">
  PerconaPGCluster.spec.instances[index].topologySpreadConstraints[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



TopologySpreadConstraint specifies how to spread matching pods among the given topology.

|                 | |
|-----------------|-|
| **Key**         | maxSkew |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | MaxSkew describes the degree to which pods may be unevenly distributed. When `whenUnsatisfiable=DoNotSchedule`, it is the maximum permitted difference between the number of matching pods in the target topology and the global minimum. The global minimum is the minimum number of matching pods in an eligible domain or zero if the number of eligible domains is less than MinDomains. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 2/2/1: In this case, the global minimum is 1. | zone1 | zone2 | zone3 | |  P P  |  P P  |   P   | - if MaxSkew is 1, incoming pod can only be scheduled to zone3 to become 2/2/2; scheduling it onto zone1(zone2) would make the ActualSkew(3-1) on zone1(zone2) violate MaxSkew(1). - if MaxSkew is 2, incoming pod can be scheduled onto any zone. When `whenUnsatisfiable=ScheduleAnyway`, it is used to give higher precedence to topologies that satisfy it. It's a required field. Default value is 1 and 0 is not allowed. |
| | |
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | TopologyKey is the key of node labels. Nodes that have a label with this key and identical values are considered to be in the same topology. We consider each <key, value> as a "bucket", and try to put balanced number of pods into each bucket. We define a domain as a particular instance of a topology. Also, we define an eligible domain as a domain whose nodes meet the requirements of nodeAffinityPolicy and nodeTaintsPolicy. e.g. If TopologyKey is "kubernetes.io/hostname", each Node is a domain of that topology. And, if TopologyKey is "topology.kubernetes.io/zone", each zone is a domain of that topology. It's a required field. |
| | |
| **Key**         | whenUnsatisfiable |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | WhenUnsatisfiable indicates how to deal with a pod if it doesn't satisfy the spread constraint. - DoNotSchedule (default) tells the scheduler not to schedule it. - ScheduleAnyway tells the scheduler to schedule the pod in any location, but giving higher precedence to topologies that would help reduce the skew. A constraint is considered "Unsatisfiable" for an incoming pod if and only if every possible node assignment for that pod would violate "MaxSkew" on some topology. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 3/1/1: | zone1 | zone2 | zone3 | | P P P |   P   |   P   | If WhenUnsatisfiable is set to DoNotSchedule, incoming pod can only be scheduled to zone2(zone3) to become 3/2/1(3/1/2) as ActualSkew(2-1) on zone2(zone3) satisfies MaxSkew(1). In other words, the cluster can still be imbalanced, but scheduler won't make it *more* imbalanced. It's a required field. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain. |
| | |
| **Key**         | matchLabelKeys |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | MatchLabelKeys is a set of pod label keys to select the pods over which spreading will be calculated. The keys are used to lookup values from the incoming pod labels, those key-value labels are ANDed with labelSelector to select the group of existing pods over which spreading will be calculated for the incoming pod. Keys that don't exist in the incoming pod labels will be ignored. A null or empty list means only match against labelSelector. |
| | |
| **Key**         | minDomains |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | MinDomains indicates a minimum number of eligible domains. When the number of eligible domains with matching topology keys is less than minDomains, Pod Topology Spread treats "global minimum" as 0, and then the calculation of Skew is performed. And when the number of eligible domains with matching topology keys equals or greater than minDomains, this value has no effect on scheduling. As a result, when the number of eligible domains is less than minDomains, scheduler won't schedule more than maxSkew Pods to those domains. If value is nil, the constraint behaves as if MinDomains is equal to 1. Valid values are integers greater than 0. When value is not nil, WhenUnsatisfiable must be DoNotSchedule. 
 For example, in a 3-zone cluster, MaxSkew is set to 2, MinDomains is set to 5 and pods with the same labelSelector spread as 2/2/2: | zone1 | zone2 | zone3 | |  P P  |  P P  |  P P  | The number of domains is less than 5(MinDomains), so "global minimum" is treated as 0. In this situation, new pod with the same labelSelector cannot be scheduled, because computed skew will be 3(3 - 0) if new Pod is scheduled to any of the three zones, it will violate MaxSkew. 
 This is a beta field and requires the MinDomainsInPodTopologySpread feature gate to be enabled (enabled by default). |
| | |
| **Key**         | nodeAffinityPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | NodeAffinityPolicy indicates how we will treat Pod's nodeAffinity/nodeSelector when calculating pod topology spread skew. Options are: - Honor: only nodes matching nodeAffinity/nodeSelector are included in the calculations. - Ignore: nodeAffinity/nodeSelector are ignored. All nodes are included in the calculations. 
 If this value is nil, the behavior is equivalent to the Honor policy. This is a alpha-level feature enabled by the NodeInclusionPolicyInPodTopologySpread feature flag. |
| | |
| **Key**         | nodeTaintsPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | NodeTaintsPolicy indicates how we will treat node taints when calculating pod topology spread skew. Options are: - Honor: nodes without taints, along with tainted nodes for which the incoming pod has a toleration, are included. - Ignore: node taints are ignored. All nodes are included. 
 If this value is nil, the behavior is equivalent to the Ignore policy. This is a alpha-level feature enabled by the NodeInclusionPolicyInPodTopologySpread feature flag. |
| | |



<h3 id="perconapgclusterspecinstancesindextopologyspreadconstraintsindexlabelselector">
  PerconaPGCluster.spec.instances[index].topologySpreadConstraints[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecinstancesindextopologyspreadconstraintsindex">↩ Parent</a></sup></sup>
</h3>



LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindextopologyspreadconstraintsindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].topologySpreadConstraints[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindextopologyspreadconstraintsindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecinstancesindexwalvolumeclaimspec">
  PerconaPGCluster.spec.instances[index].walVolumeClaimSpec
  <sup><sup><a href="#perconapgclusterspecinstancesindex">↩ Parent</a></sup></sup>
</h3>



Defines a separate PersistentVolumeClaim for PostgreSQL's write-ahead log. More info: https://www.postgresql.org/docs/current/wal.html

|                 | |
|-----------------|-|
| **Key**         | accessModes |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | accessModes contains the desired access modes the volume should have. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#access-modes-1 |
| | |
| **Key**         | dataSource |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field. |
| | |
| **Key**         | dataSourceRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled. |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources |
| | |
| **Key**         | selector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | selector is a label query over volumes to consider for binding. |
| | |
| **Key**         | storageClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | storageClassName is the name of the StorageClass required by the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#class-1 |
| | |
| **Key**         | volumeMode |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeMode defines what type of volume is required by the claim. Value of Filesystem is implied when not included in claim spec. |
| | |
| **Key**         | volumeName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeName is the binding reference to the PersistentVolume backing this claim. |
| | |



<h3 id="perconapgclusterspecinstancesindexwalvolumeclaimspecdatasource">
  PerconaPGCluster.spec.instances[index].walVolumeClaimSpec.dataSource
  <sup><sup><a href="#perconapgclusterspecinstancesindexwalvolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecinstancesindexwalvolumeclaimspecdatasourceref">
  PerconaPGCluster.spec.instances[index].walVolumeClaimSpec.dataSourceRef
  <sup><sup><a href="#perconapgclusterspecinstancesindexwalvolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecinstancesindexwalvolumeclaimspecresources">
  PerconaPGCluster.spec.instances[index].walVolumeClaimSpec.resources
  <sup><sup><a href="#perconapgclusterspecinstancesindexwalvolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecinstancesindexwalvolumeclaimspecselector">
  PerconaPGCluster.spec.instances[index].walVolumeClaimSpec.selector
  <sup><sup><a href="#perconapgclusterspecinstancesindexwalvolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



selector is a label query over volumes to consider for binding.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecinstancesindexwalvolumeclaimspecselectormatchexpressionsindex">
  PerconaPGCluster.spec.instances[index].walVolumeClaimSpec.selector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecinstancesindexwalvolumeclaimspecselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasource">
  PerconaPGCluster.spec.dataSource
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



Specifies a data source for bootstrapping the PostgreSQL cluster.

|                 | |
|-----------------|-|
| **Key**         | pgbackrest |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines a pgBackRest cloud-based data source that can be used to pre-populate the the PostgreSQL data directory for a new PostgreSQL cluster using a pgBackRest restore. The PGBackRest field is incompatible with the PostgresCluster field: only one data source can be used for pre-populating a new PostgreSQL cluster |
| | |
| **Key**         | postgresCluster |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines a pgBackRest data source that can be used to pre-populate the PostgreSQL data directory for a new PostgreSQL cluster using a pgBackRest restore. The PGBackRest field is incompatible with the PostgresCluster field: only one data source can be used for pre-populating a new PostgreSQL cluster |
| | |
| **Key**         | volumes |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines any existing volumes to reuse for this PostgresCluster. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrest">
  PerconaPGCluster.spec.dataSource.pgbackrest
  <sup><sup><a href="#perconapgclusterspecdatasource">↩ Parent</a></sup></sup>
</h3>



Defines a pgBackRest cloud-based data source that can be used to pre-populate the the PostgreSQL data directory for a new PostgreSQL cluster using a pgBackRest restore. The PGBackRest field is incompatible with the PostgresCluster field: only one data source can be used for pre-populating a new PostgreSQL cluster

|                 | |
|-----------------|-|
| **Key**         | repo |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Defines a pgBackRest repository |
| | |
| **Key**         | stanza |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of an existing pgBackRest stanza to use as the data source for the new PostgresCluster. Defaults to `db` if not provided. |
| | |
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | configuration |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Projected volumes containing custom pgBackRest configuration.  These files are mounted under "/etc/pgbackrest/conf.d" alongside any pgBackRest configuration generated by the PostgreSQL Operator: https://pgbackrest.org/configuration.html |
| | |
| **Key**         | global |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | Global pgBackRest configuration settings.  These settings are included in the "global" section of the pgBackRest configuration generated by the PostgreSQL Operator, and then mounted under "/etc/pgbackrest/conf.d": https://pgbackrest.org/configuration.html |
| | |
| **Key**         | options |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command line options to include when running the pgBackRest restore command. https://pgbackrest.org/command.html#command-restore |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the pgBackRest restore Job pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource requirements for the pgBackRest restore Job. |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepo">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrest">↩ Parent</a></sup></sup>
</h3>



Defines a pgBackRest repository

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the the repository |
| | |
| **Key**         | azure |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents a pgBackRest repository that is created using Azure storage |
| | |
| **Key**         | gcs |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents a pgBackRest repository that is created using Google Cloud Storage |
| | |
| **Key**         | s3 |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | RepoS3 represents a pgBackRest repository that is created using AWS S3 (or S3-compatible) storage |
| | |
| **Key**         | schedules |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the schedules for the pgBackRest backups Full, Differential and Incremental backup types are supported: https://pgbackrest.org/user-guide.html#concept/backup |
| | |
| **Key**         | volume |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents a pgBackRest repository that is created using a PersistentVolumeClaim |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepoazure">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.azure
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepo">↩ Parent</a></sup></sup>
</h3>



Represents a pgBackRest repository that is created using Azure storage

|                 | |
|-----------------|-|
| **Key**         | container |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The Azure container utilized for the repository |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepogcs">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.gcs
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepo">↩ Parent</a></sup></sup>
</h3>



Represents a pgBackRest repository that is created using Google Cloud Storage

|                 | |
|-----------------|-|
| **Key**         | bucket |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The GCS bucket utilized for the repository |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepos3">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.s3
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepo">↩ Parent</a></sup></sup>
</h3>



RepoS3 represents a pgBackRest repository that is created using AWS S3 (or S3-compatible) storage

|                 | |
|-----------------|-|
| **Key**         | bucket |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The S3 bucket utilized for the repository |
| | |
| **Key**         | endpoint |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | A valid endpoint corresponding to the specified region |
| | |
| **Key**         | region |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The region corresponding to the S3 bucket |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestreposchedules">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.schedules
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepo">↩ Parent</a></sup></sup>
</h3>



Defines the schedules for the pgBackRest backups Full, Differential and Incremental backup types are supported: https://pgbackrest.org/user-guide.html#concept/backup

|                 | |
|-----------------|-|
| **Key**         | differential |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the Cron schedule for a differential pgBackRest backup. Follows the standard Cron schedule syntax: https://k8s.io/docs/concepts/workloads/controllers/cron-jobs/#cron-schedule-syntax |
| | |
| **Key**         | full |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the Cron schedule for a full pgBackRest backup. Follows the standard Cron schedule syntax: https://k8s.io/docs/concepts/workloads/controllers/cron-jobs/#cron-schedule-syntax |
| | |
| **Key**         | incremental |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the Cron schedule for an incremental pgBackRest backup. Follows the standard Cron schedule syntax: https://k8s.io/docs/concepts/workloads/controllers/cron-jobs/#cron-schedule-syntax |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolume">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepo">↩ Parent</a></sup></sup>
</h3>



Represents a pgBackRest repository that is created using a PersistentVolumeClaim

|                 | |
|-----------------|-|
| **Key**         | volumeClaimSpec |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Defines a PersistentVolumeClaim spec used to create and/or bind a volume |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspec">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume.volumeClaimSpec
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepovolume">↩ Parent</a></sup></sup>
</h3>



Defines a PersistentVolumeClaim spec used to create and/or bind a volume

|                 | |
|-----------------|-|
| **Key**         | accessModes |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | accessModes contains the desired access modes the volume should have. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#access-modes-1 |
| | |
| **Key**         | dataSource |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field. |
| | |
| **Key**         | dataSourceRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled. |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources |
| | |
| **Key**         | selector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | selector is a label query over volumes to consider for binding. |
| | |
| **Key**         | storageClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | storageClassName is the name of the StorageClass required by the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#class-1 |
| | |
| **Key**         | volumeMode |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeMode defines what type of volume is required by the claim. Value of Filesystem is implied when not included in claim spec. |
| | |
| **Key**         | volumeName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeName is the binding reference to the PersistentVolume backing this claim. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspecdatasource">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume.volumeClaimSpec.dataSource
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSource field can be used to specify either: * An existing VolumeSnapshot object (snapshot.storage.k8s.io/VolumeSnapshot) * An existing PVC (PersistentVolumeClaim) If the provisioner or an external controller can support the specified data source, it will create a new volume based on the contents of the specified data source. If the AnyVolumeDataSource feature gate is enabled, this field will always have the same contents as the DataSourceRef field.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspecdatasourceref">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume.volumeClaimSpec.dataSourceRef
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



dataSourceRef specifies the object from which to populate the volume with data, if a non-empty volume is desired. This may be any local object from a non-empty API group (non core object) or a PersistentVolumeClaim object. When this field is specified, volume binding will only succeed if the type of the specified object matches some installed volume populator or dynamic provisioner. This field will replace the functionality of the DataSource field and as such if both fields are non-empty, they must have the same value. For backwards compatibility, both fields (DataSource and DataSourceRef) will be set to the same value automatically if one of them is empty and the other is non-empty. There are two important differences between DataSource and DataSourceRef: * While DataSource only allows two specific types of objects, DataSourceRef allows any non-core object, as well as PersistentVolumeClaim objects. * While DataSource ignores disallowed values (dropping them), DataSourceRef preserves all values, and generates an error if a disallowed value is specified. (Beta) Using this field requires the AnyVolumeDataSource feature gate to be enabled.

|                 | |
|-----------------|-|
| **Key**         | kind |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Kind is the type of resource being referenced |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of resource being referenced |
| | |
| **Key**         | apiGroup |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIGroup is the group for the resource being referenced. If APIGroup is not specified, the specified Kind must be in the core API group. For any other third-party types, APIGroup is required. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspecresources">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume.volumeClaimSpec.resources
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



resources represents the minimum resources the volume should have. If RecoverVolumeExpansionFailure feature is enabled users are allowed to specify resource requirements that are lower than previous value but must still be higher than capacity recorded in the status field of the claim. More info: https://kubernetes.io/docs/concepts/storage/persistent-volumes#resources

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspecselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume.volumeClaimSpec.selector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspec">↩ Parent</a></sup></sup>
</h3>



selector is a label query over volumes to consider for binding.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspecselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.repo.volume.volumeClaimSpec.selector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestrepovolumevolumeclaimspecselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinity">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrest">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinity">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinity">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinity">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestaffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrest">↩ Parent</a></sup></sup>
</h3>



Projection that may be projected along with other supported volume types

|                 | |
|-----------------|-|
| **Key**         | configMap |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | configMap information about the configMap data to project |
| | |
| **Key**         | downwardAPI |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | downwardAPI information about the downwardAPI data to project |
| | |
| **Key**         | secret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | secret information about the secret data to project |
| | |
| **Key**         | serviceAccountToken |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | serviceAccountToken is information about the serviceAccountToken data to project |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexconfigmap">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].configMap
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



configMap information about the configMap data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced ConfigMap will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the ConfigMap, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional specify whether the ConfigMap or its keys must be defined |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexconfigmapitemsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].configMap.items[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindexconfigmap">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapi">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].downwardAPI
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



downwardAPI information about the downwardAPI data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Items is a list of DownwardAPIVolume file |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapiitemsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].downwardAPI.items[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapi">↩ Parent</a></sup></sup>
</h3>



DownwardAPIVolumeFile represents information to create the file containing the pod field

|                 | |
|-----------------|-|
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: Path is  the relative path name of the file to be created. Must not be absolute or contain the '..' path. Must be utf-8 encoded. The first item of the relative path must not start with '..' |
| | |
| **Key**         | fieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Required: Selects a field of the pod: only annotations, labels, name and namespace are supported. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: mode bits used to set permissions on this file, must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |
| **Key**         | resourceFieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapiitemsindexfieldref">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].downwardAPI.items[index].fieldRef
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapiitemsindex">↩ Parent</a></sup></sup>
</h3>



Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.

|                 | |
|-----------------|-|
| **Key**         | fieldPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path of the field to select in the specified API version. |
| | |
| **Key**         | apiVersion |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Version of the schema the FieldPath is written in terms of, defaults to "v1". |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapiitemsindexresourcefieldref">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].downwardAPI.items[index].resourceFieldRef
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindexdownwardapiitemsindex">↩ Parent</a></sup></sup>
</h3>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.

|                 | |
|-----------------|-|
| **Key**         | resource |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: resource to select |
| | |
| **Key**         | containerName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container name: required for volumes, optional for env vars |
| | |
| **Key**         | divisor |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies the output format of the exposed resources, defaults to "1" |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexsecret">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].secret
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



secret information about the secret data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexsecretitemsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].secret.items[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindexsecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestconfigurationindexserviceaccounttoken">
  PerconaPGCluster.spec.dataSource.pgbackrest.configuration[index].serviceAccountToken
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrestconfigurationindex">↩ Parent</a></sup></sup>
</h3>



serviceAccountToken is information about the serviceAccountToken data to project

|                 | |
|-----------------|-|
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the path relative to the mount point of the file to project the token into. |
| | |
| **Key**         | audience |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | audience is the intended audience of the token. A recipient of a token must identify itself with an identifier specified in the audience of the token, and otherwise should reject the token. The audience defaults to the identifier of the apiserver. |
| | |
| **Key**         | expirationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | expirationSeconds is the requested duration of validity of the service account token. As the token approaches expiration, the kubelet volume plugin will proactively rotate the service account token. The kubelet will start trying to rotate the token if the token is older than 80 percent of its time to live or if the token is older than 24 hours.Defaults to 1 hour and must be at least 10 minutes. |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackrestresources">
  PerconaPGCluster.spec.dataSource.pgbackrest.resources
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrest">↩ Parent</a></sup></sup>
</h3>



Resource requirements for the pgBackRest restore Job.

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecdatasourcepgbackresttolerationsindex">
  PerconaPGCluster.spec.dataSource.pgbackrest.tolerations[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepgbackrest">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgrescluster">
  PerconaPGCluster.spec.dataSource.postgresCluster
  <sup><sup><a href="#perconapgclusterspecdatasource">↩ Parent</a></sup></sup>
</h3>



Defines a pgBackRest data source that can be used to pre-populate the PostgreSQL data directory for a new PostgreSQL cluster using a pgBackRest restore. The PGBackRest field is incompatible with the PostgresCluster field: only one data source can be used for pre-populating a new PostgreSQL cluster

|                 | |
|-----------------|-|
| **Key**         | repoName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the pgBackRest repo within the source PostgresCluster that contains the backups that should be utilized to perform a pgBackRest restore when initializing the data source for the new PostgresCluster. |
| | |
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | clusterName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The name of an existing PostgresCluster to use as the data source for the new PostgresCluster. Defaults to the name of the PostgresCluster being created if not provided. |
| | |
| **Key**         | clusterNamespace |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The namespace of the cluster specified as the data source using the clusterName field. Defaults to the namespace of the PostgresCluster being created if not provided. |
| | |
| **Key**         | options |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command line options to include when running the pgBackRest restore command. https://pgbackrest.org/command.html#command-restore |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the pgBackRest restore Job pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Resource requirements for the pgBackRest restore Job. |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinity">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgrescluster">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of the pgBackRest restore Job. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinity">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinity">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinity">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgresclusteraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclusterresources">
  PerconaPGCluster.spec.dataSource.postgresCluster.resources
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgrescluster">↩ Parent</a></sup></sup>
</h3>



Resource requirements for the pgBackRest restore Job.

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecdatasourcepostgresclustertolerationsindex">
  PerconaPGCluster.spec.dataSource.postgresCluster.tolerations[index]
  <sup><sup><a href="#perconapgclusterspecdatasourcepostgrescluster">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecdatasourcevolumes">
  PerconaPGCluster.spec.dataSource.volumes
  <sup><sup><a href="#perconapgclusterspecdatasource">↩ Parent</a></sup></sup>
</h3>



Defines any existing volumes to reuse for this PostgresCluster.

|                 | |
|-----------------|-|
| **Key**         | pgBackRestVolume |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the existing pgBackRest repo volume and directory to use in the current PostgresCluster. |
| | |
| **Key**         | pgDataVolume |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the existing pgData volume and directory to use in the current PostgresCluster. |
| | |
| **Key**         | pgWALVolume |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Defines the existing pg_wal volume and directory to use in the current PostgresCluster. Note that a defined pg_wal volume MUST be accompanied by a pgData volume. |
| | |



<h3 id="perconapgclusterspecdatasourcevolumespgbackrestvolume">
  PerconaPGCluster.spec.dataSource.volumes.pgBackRestVolume
  <sup><sup><a href="#perconapgclusterspecdatasourcevolumes">↩ Parent</a></sup></sup>
</h3>



Defines the existing pgBackRest repo volume and directory to use in the current PostgresCluster.

|                 | |
|-----------------|-|
| **Key**         | pvcName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The existing PVC name. |
| | |
| **Key**         | directory |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The existing directory. When not set, a move Job is not created for the associated volume. |
| | |



<h3 id="perconapgclusterspecdatasourcevolumespgdatavolume">
  PerconaPGCluster.spec.dataSource.volumes.pgDataVolume
  <sup><sup><a href="#perconapgclusterspecdatasourcevolumes">↩ Parent</a></sup></sup>
</h3>



Defines the existing pgData volume and directory to use in the current PostgresCluster.

|                 | |
|-----------------|-|
| **Key**         | pvcName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The existing PVC name. |
| | |
| **Key**         | directory |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The existing directory. When not set, a move Job is not created for the associated volume. |
| | |



<h3 id="perconapgclusterspecdatasourcevolumespgwalvolume">
  PerconaPGCluster.spec.dataSource.volumes.pgWALVolume
  <sup><sup><a href="#perconapgclusterspecdatasourcevolumes">↩ Parent</a></sup></sup>
</h3>



Defines the existing pg_wal volume and directory to use in the current PostgresCluster. Note that a defined pg_wal volume MUST be accompanied by a pgData volume.

|                 | |
|-----------------|-|
| **Key**         | pvcName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The existing PVC name. |
| | |
| **Key**         | directory |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The existing directory. When not set, a move Job is not created for the associated volume. |
| | |



<h3 id="perconapgclusterspecdatabaseinitsql">
  PerconaPGCluster.spec.databaseInitSQL
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



DatabaseInitSQL defines a ConfigMap containing custom SQL that will be run after the cluster is initialized. This ConfigMap must be in the same namespace as the cluster.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Key is the ConfigMap data key that points to a SQL string |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name is the name of a ConfigMap |
| | |



<h3 id="perconapgclusterspecexpose">
  PerconaPGCluster.spec.expose
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



Specification of the service that exposes the PostgreSQL primary instance.

|                 | |
|-----------------|-|
| **Key**         | annotations |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | labels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | nodePort |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The port on which this service is exposed when type is NodePort or LoadBalancer. Value must be in-range and not in use or the operation will fail. If unspecified, a port will be allocated if this Service requires one. - https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport |
| | |
| **Key**         | type |
| **Value**       | enum |
| **Required**    | false |
| **Example**     | |
| **Description** | More info: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types |
| | |



<h3 id="perconapgclusterspecimagepullsecretsindex">
  PerconaPGCluster.spec.imagePullSecrets[index]
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



LocalObjectReference contains enough information to let you locate the referenced object inside the same namespace.

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |



<h3 id="perconapgclusterspecpatroni">
  PerconaPGCluster.spec.patroni
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | dynamicConfiguration |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Patroni dynamic configuration settings. Changes to this value will be automatically reloaded without validation. Changes to certain PostgreSQL parameters cause PostgreSQL to restart. More info: https://patroni.readthedocs.io/en/latest/SETTINGS.html |
| | |
| **Key**         | leaderLeaseDurationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TTL of the cluster leader lock. "Think of it as the length of time before initiation of the automatic failover process." Changing this value causes PostgreSQL to restart. |
| | |
| **Key**         | port |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The port on which Patroni should listen. Changing this value causes PostgreSQL to restart. |
| | |
| **Key**         | switchover |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Switchover gives options to perform ad hoc switchovers in a PostgresCluster. |
| | |
| **Key**         | syncPeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The interval for refreshing the leader lock and applying dynamicConfiguration. Must be less than leaderLeaseDurationSeconds. Changing this value causes PostgreSQL to restart. |
| | |



<h3 id="perconapgclusterspecpatroniswitchover">
  PerconaPGCluster.spec.patroni.switchover
  <sup><sup><a href="#perconapgclusterspecpatroni">↩ Parent</a></sup></sup>
</h3>



Switchover gives options to perform ad hoc switchovers in a PostgresCluster.

|                 | |
|-----------------|-|
| **Key**         | enabled |
| **Value**       | boolean |
| **Required**    | true |
| **Example**     | |
| **Description** | Whether or not the operator should allow switchovers in a PostgresCluster |
| | |
| **Key**         | targetInstance |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The instance that should become primary during a switchover. This field is optional when Type is "Switchover" and required when Type is "Failover". When it is not specified, a healthy replica is automatically selected. |
| | |
| **Key**         | type |
| **Value**       | enum |
| **Required**    | false |
| **Example**     | |
| **Description** | Type of switchover to perform. Valid options are Switchover and Failover. "Switchover" changes the primary instance of a healthy PostgresCluster. "Failover" forces a particular instance to be primary, regardless of other factors. A TargetInstance must be specified to failover. NOTE: The Failover type is reserved as the "last resort" case. |
| | |



<h3 id="perconapgclusterspecpmm">
  PerconaPGCluster.spec.pmm
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



The specification of PMM sidecars.

|                 | |
|-----------------|-|
| **Key**         | enabled |
| **Value**       | boolean |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | image |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | containerSecurityContext |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | SecurityContext holds security configuration that will be applied to a container. Some fields are present in both SecurityContext and PodSecurityContext.  When both are set, the values in SecurityContext take precedence. |
| | |
| **Key**         | imagePullPolicy |
| **Value**       | enum |
| **Required**    | false |
| **Example**     | |
| **Description** | ImagePullPolicy is used to determine when Kubernetes will attempt to pull (download) container images. More info: https://kubernetes.io/docs/concepts/containers/images/#image-pull-policy |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Compute resources of a PMM container. |
| | |
| **Key**         | runtimeClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | secret |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | serverHost |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterspecpmmcontainersecuritycontext">
  PerconaPGCluster.spec.pmm.containerSecurityContext
  <sup><sup><a href="#perconapgclusterspecpmm">↩ Parent</a></sup></sup>
</h3>



SecurityContext holds security configuration that will be applied to a container. Some fields are present in both SecurityContext and PodSecurityContext.  When both are set, the values in SecurityContext take precedence.

|                 | |
|-----------------|-|
| **Key**         | allowPrivilegeEscalation |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | AllowPrivilegeEscalation controls whether a process can gain more privileges than its parent process. This bool directly controls if the no_new_privs flag will be set on the container process. AllowPrivilegeEscalation is true always when the container is: 1) run as Privileged 2) has CAP_SYS_ADMIN Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | capabilities |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | privileged |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Run container in privileged mode. Processes in privileged containers are essentially equivalent to root on the host. Defaults to false. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | procMount |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | procMount denotes the type of proc mount to use for the containers. The default is DefaultProcMount which uses the container runtime defaults for readonly paths and masked paths. This requires the ProcMountType feature flag to be enabled. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | readOnlyRootFilesystem |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container has a read-only root filesystem. Default is false. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | runAsGroup |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | runAsNonRoot |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. |
| | |
| **Key**         | runAsUser |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | seLinuxOptions |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | seccompProfile |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The seccomp options to use by this container. If seccomp options are provided at both the pod & container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | windowsOptions |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux. |
| | |



<h3 id="perconapgclusterspecpmmcontainersecuritycontextcapabilities">
  PerconaPGCluster.spec.pmm.containerSecurityContext.capabilities
  <sup><sup><a href="#perconapgclusterspecpmmcontainersecuritycontext">↩ Parent</a></sup></sup>
</h3>



The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | add |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Added capabilities |
| | |
| **Key**         | drop |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Removed capabilities |
| | |



<h3 id="perconapgclusterspecpmmcontainersecuritycontextselinuxoptions">
  PerconaPGCluster.spec.pmm.containerSecurityContext.seLinuxOptions
  <sup><sup><a href="#perconapgclusterspecpmmcontainersecuritycontext">↩ Parent</a></sup></sup>
</h3>



The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | level |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Level is SELinux level label that applies to the container. |
| | |
| **Key**         | role |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Role is a SELinux role label that applies to the container. |
| | |
| **Key**         | type |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Type is a SELinux type label that applies to the container. |
| | |
| **Key**         | user |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | User is a SELinux user label that applies to the container. |
| | |



<h3 id="perconapgclusterspecpmmcontainersecuritycontextseccompprofile">
  PerconaPGCluster.spec.pmm.containerSecurityContext.seccompProfile
  <sup><sup><a href="#perconapgclusterspecpmmcontainersecuritycontext">↩ Parent</a></sup></sup>
</h3>



The seccomp options to use by this container. If seccomp options are provided at both the pod & container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | type |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied. |
| | |
| **Key**         | localhostProfile |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet's configured seccomp profile location. Must only be set if type is "Localhost". |
| | |



<h3 id="perconapgclusterspecpmmcontainersecuritycontextwindowsoptions">
  PerconaPGCluster.spec.pmm.containerSecurityContext.windowsOptions
  <sup><sup><a href="#perconapgclusterspecpmmcontainersecuritycontext">↩ Parent</a></sup></sup>
</h3>



The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.

|                 | |
|-----------------|-|
| **Key**         | gmsaCredentialSpec |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field. |
| | |
| **Key**         | gmsaCredentialSpecName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | GMSACredentialSpecName is the name of the GMSA credential spec to use. |
| | |
| **Key**         | hostProcess |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | HostProcess determines if a container should be run as a 'Host Process' container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod's containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true. |
| | |
| **Key**         | runAsUserName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. |
| | |



<h3 id="perconapgclusterspecpmmresources">
  PerconaPGCluster.spec.pmm.resources
  <sup><sup><a href="#perconapgclusterspecpmm">↩ Parent</a></sup></sup>
</h3>



Compute resources of a PMM container.

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecproxy">
  PerconaPGCluster.spec.proxy
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



The specification of a proxy that connects to PostgreSQL.

|                 | |
|-----------------|-|
| **Key**         | pgBouncer |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Defines a PgBouncer proxy and connection pooler. |
| | |



<h3 id="perconapgclusterspecproxypgbouncer">
  PerconaPGCluster.spec.proxy.pgBouncer
  <sup><sup><a href="#perconapgclusterspecproxy">↩ Parent</a></sup></sup>
</h3>



Defines a PgBouncer proxy and connection pooler.

|                 | |
|-----------------|-|
| **Key**         | affinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheduling constraints of a PgBouncer pod. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node |
| | |
| **Key**         | config |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Configuration settings for the PgBouncer process. Changes to any of these values will be automatically reloaded without validation. Be careful, as you may put PgBouncer into an unusable state. More info: https://www.pgbouncer.org/usage.html#reload |
| | |
| **Key**         | customTLSSecret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A secret projection containing a certificate and key with which to encrypt connections to PgBouncer. The "tls.crt", "tls.key", and "ca.crt" paths must be PEM-encoded certificates and keys. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/configuration/secret/#projection-of-secret-keys-to-specific-paths |
| | |
| **Key**         | expose |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Specification of the service that exposes PgBouncer. |
| | |
| **Key**         | image |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of a container image that can run PgBouncer 1.15 or newer. Changing this value causes PgBouncer to restart. The image may also be set using the RELATED_IMAGE_PGBOUNCER environment variable. More info: https://kubernetes.io/docs/concepts/containers/images |
| | |
| **Key**         | metadata |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Metadata contains metadata for PostgresCluster resources |
| | |
| **Key**         | minAvailable |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum number of pods that should be available at a time. Defaults to one when the replicas field is greater than one. |
| | |
| **Key**         | port |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Port on which PgBouncer should listen for client connections. Changing this value causes PgBouncer to restart. |
| | |
| **Key**         | priorityClassName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Priority class name for the pgBouncer pod. Changing this value causes PostgreSQL to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/ |
| | |
| **Key**         | replicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of desired PgBouncer pods. |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Compute resources of a PgBouncer container. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers |
| | |
| **Key**         | sidecars |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom sidecars for a PgBouncer pod. Changing this value causes PgBouncer to restart. |
| | |
| **Key**         | tolerations |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Tolerations of a PgBouncer pod. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration |
| | |
| **Key**         | topologySpreadConstraints |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Topology spread constraints of a PgBouncer pod. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-topology-spread-constraints/ |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinity">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



Scheduling constraints of a PgBouncer pod. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node

|                 | |
|-----------------|-|
| **Key**         | nodeAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes node affinity scheduling rules for the pod. |
| | |
| **Key**         | podAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)). |
| | |
| **Key**         | podAntiAffinity |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)). |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinity">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinity">↩ Parent</a></sup></sup>
</h3>



Describes node affinity scheduling rules for the pod.

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node matches the corresponding matchExpressions; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



An empty preferred scheduling term matches all objects with implicit weight 0 (i.e. it's a no-op). A null preferred scheduling term matches no objects (i.e. is also a no-op).

|                 | |
|-----------------|-|
| **Key**         | preference |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | A node selector term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Weight associated with matching the corresponding nodeSelectorTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A node selector term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreferencematchfieldsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].preference.matchFields[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinitypreferredduringschedulingignoredduringexecutionindexpreference">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecution">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinity">↩ Parent</a></sup></sup>
</h3>



If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to an update), the system may or may not try to eventually evict the pod from its node.

|                 | |
|-----------------|-|
| **Key**         | nodeSelectorTerms |
| **Value**       | []object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A list of node selector terms. The terms are ORed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecution">↩ Parent</a></sup></sup>
</h3>



A null or empty node selector term matches no objects. The requirements of them are ANDed. The TopologySelectorTerm type implements a subset of the NodeSelectorTerm.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's labels. |
| | |
| **Key**         | matchFields |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | A list of node selector requirements by node's fields. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindexmatchfieldsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.nodeAffinity.requiredDuringSchedulingIgnoredDuringExecution.nodeSelectorTerms[index].matchFields[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitynodeaffinityrequiredduringschedulingignoredduringexecutionnodeselectortermsindex">↩ Parent</a></sup></sup>
</h3>



A node selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists, DoesNotExist. Gt, and Lt. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | An array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. If the operator is Gt or Lt, the values array must have a single element, which will be interpreted as an integer. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinity">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod affinity scheduling rules (e.g. co-locate this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinity">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinity">↩ Parent</a></sup></sup>
</h3>



Describes pod anti-affinity scheduling rules (e.g. avoid putting this pod in the same node, zone, etc. as some other pod(s)).

|                 | |
|-----------------|-|
| **Key**         | preferredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | The scheduler will prefer to schedule pods to nodes that satisfy the anti-affinity expressions specified by this field, but it may choose a node that violates one or more of the expressions. The node that is most preferred is the one with the greatest sum of weights, i.e. for each node that meets all of the scheduling requirements (resource request, requiredDuringScheduling anti-affinity expressions, etc.), compute a sum by iterating through the elements of this field and adding "weight" to the sum if the node has pods which matches the corresponding podAffinityTerm; the node(s) with the highest sum are the most preferred. |
| | |
| **Key**         | requiredDuringSchedulingIgnoredDuringExecution |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | If the anti-affinity requirements specified by this field are not met at scheduling time, the pod will not be scheduled onto the node. If the anti-affinity requirements specified by this field cease to be met at some point during pod execution (e.g. due to a pod label update), the system may or may not try to eventually evict the pod from its node. When there are multiple elements, the lists of nodes corresponding to each podAffinityTerm are intersected, i.e. all terms must be satisfied. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



The weights of all of the matched WeightedPodAffinityTerm fields are added per-node to find the most preferred node(s)

|                 | |
|-----------------|-|
| **Key**         | podAffinityTerm |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** | Required. A pod affinity term, associated with the corresponding weight. |
| | |
| **Key**         | weight |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | weight associated with matching the corresponding podAffinityTerm, in the range 1-100. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



Required. A pod affinity term, associated with the corresponding weight.

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinityterm">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.preferredDuringSchedulingIgnoredDuringExecution[index].podAffinityTerm.namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinitypreferredduringschedulingignoredduringexecutionindexpodaffinitytermnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinity">↩ Parent</a></sup></sup>
</h3>



Defines a set of pods (namely those matching the labelSelector relative to the given namespace(s)) that this pod should be co-located (affinity) or not co-located (anti-affinity) with, where co-located is defined as running on a node whose value of the label with key <topologyKey> matches that of any node on which a pod of the set of pods is running

|                 | |
|-----------------|-|
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This pod should be co-located (affinity) or not co-located (anti-affinity) with the pods matching the labelSelector in the specified namespaces, where co-located is defined as running on a node whose value of the label with key topologyKey matches that of any node on which any of the selected pods is running. Empty topologyKey is not allowed. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over a set of resources, in this case pods. |
| | |
| **Key**         | namespaceSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces. |
| | |
| **Key**         | namespaces |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | namespaces specifies a static list of namespace names that the term applies to. The term is applied to the union of the namespaces listed in this field and the ones selected by namespaceSelector. null or empty namespaces list and null namespaceSelector means "this pod's namespace". |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over a set of resources, in this case pods.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindex">↩ Parent</a></sup></sup>
</h3>



A label query over the set of namespaces that the term applies to. The term is applied to the union of the namespaces selected by this field and the ones listed in the namespaces field. null selector and null or empty namespaces list means "this pod's namespace". An empty selector ({}) matches all namespaces.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.affinity.podAntiAffinity.requiredDuringSchedulingIgnoredDuringExecution[index].namespaceSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbounceraffinitypodantiaffinityrequiredduringschedulingignoredduringexecutionindexnamespaceselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfig">
  PerconaPGCluster.spec.proxy.pgBouncer.config
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



Configuration settings for the PgBouncer process. Changes to any of these values will be automatically reloaded without validation. Be careful, as you may put PgBouncer into an unusable state. More info: https://www.pgbouncer.org/usage.html#reload

|                 | |
|-----------------|-|
| **Key**         | databases |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | PgBouncer database definitions. The key is the database requested by a client while the value is a libpq-styled connection string. The special key "*" acts as a fallback. When this field is empty, PgBouncer is configured with a single "*" entry that connects to the primary PostgreSQL instance. More info: https://www.pgbouncer.org/config.html#section-databases |
| | |
| **Key**         | files |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Files to mount under "/etc/pgbouncer". When specified, settings in the "pgbouncer.ini" file are loaded before all others. From there, other files may be included by absolute path. Changing these references causes PgBouncer to restart, but changes to the file contents are automatically reloaded. More info: https://www.pgbouncer.org/config.html#include-directive |
| | |
| **Key**         | global |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | Settings that apply to the entire PgBouncer process. More info: https://www.pgbouncer.org/config.html |
| | |
| **Key**         | users |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | Connection settings specific to particular users. More info: https://www.pgbouncer.org/config.html#section-users |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindex">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfig">↩ Parent</a></sup></sup>
</h3>



Projection that may be projected along with other supported volume types

|                 | |
|-----------------|-|
| **Key**         | configMap |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | configMap information about the configMap data to project |
| | |
| **Key**         | downwardAPI |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | downwardAPI information about the downwardAPI data to project |
| | |
| **Key**         | secret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | secret information about the secret data to project |
| | |
| **Key**         | serviceAccountToken |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | serviceAccountToken is information about the serviceAccountToken data to project |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexconfigmap">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].configMap
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindex">↩ Parent</a></sup></sup>
</h3>



configMap information about the configMap data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced ConfigMap will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the ConfigMap, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional specify whether the ConfigMap or its keys must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexconfigmapitemsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].configMap.items[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindexconfigmap">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapi">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].downwardAPI
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindex">↩ Parent</a></sup></sup>
</h3>



downwardAPI information about the downwardAPI data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Items is a list of DownwardAPIVolume file |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapiitemsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].downwardAPI.items[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapi">↩ Parent</a></sup></sup>
</h3>



DownwardAPIVolumeFile represents information to create the file containing the pod field

|                 | |
|-----------------|-|
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: Path is  the relative path name of the file to be created. Must not be absolute or contain the '..' path. Must be utf-8 encoded. The first item of the relative path must not start with '..' |
| | |
| **Key**         | fieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Required: Selects a field of the pod: only annotations, labels, name and namespace are supported. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: mode bits used to set permissions on this file, must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |
| **Key**         | resourceFieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported. |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapiitemsindexfieldref">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].downwardAPI.items[index].fieldRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapiitemsindex">↩ Parent</a></sup></sup>
</h3>



Required: Selects a field of the pod: only annotations, labels, name and namespace are supported.

|                 | |
|-----------------|-|
| **Key**         | fieldPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path of the field to select in the specified API version. |
| | |
| **Key**         | apiVersion |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Version of the schema the FieldPath is written in terms of, defaults to "v1". |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapiitemsindexresourcefieldref">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].downwardAPI.items[index].resourceFieldRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindexdownwardapiitemsindex">↩ Parent</a></sup></sup>
</h3>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, requests.cpu and requests.memory) are currently supported.

|                 | |
|-----------------|-|
| **Key**         | resource |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: resource to select |
| | |
| **Key**         | containerName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container name: required for volumes, optional for env vars |
| | |
| **Key**         | divisor |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies the output format of the exposed resources, defaults to "1" |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexsecret">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].secret
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindex">↩ Parent</a></sup></sup>
</h3>



secret information about the secret data to project

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexsecretitemsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].secret.items[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindexsecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecproxypgbouncerconfigfilesindexserviceaccounttoken">
  PerconaPGCluster.spec.proxy.pgBouncer.config.files[index].serviceAccountToken
  <sup><sup><a href="#perconapgclusterspecproxypgbouncerconfigfilesindex">↩ Parent</a></sup></sup>
</h3>



serviceAccountToken is information about the serviceAccountToken data to project

|                 | |
|-----------------|-|
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the path relative to the mount point of the file to project the token into. |
| | |
| **Key**         | audience |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | audience is the intended audience of the token. A recipient of a token must identify itself with an identifier specified in the audience of the token, and otherwise should reject the token. The audience defaults to the identifier of the apiserver. |
| | |
| **Key**         | expirationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | expirationSeconds is the requested duration of validity of the service account token. As the token approaches expiration, the kubelet volume plugin will proactively rotate the service account token. The kubelet will start trying to rotate the token if the token is older than 80 percent of its time to live or if the token is older than 24 hours.Defaults to 1 hour and must be at least 10 minutes. |
| | |



<h3 id="perconapgclusterspecproxypgbouncercustomtlssecret">
  PerconaPGCluster.spec.proxy.pgBouncer.customTLSSecret
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



A secret projection containing a certificate and key with which to encrypt connections to PgBouncer. The "tls.crt", "tls.key", and "ca.crt" paths must be PEM-encoded certificates and keys. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/configuration/secret/#projection-of-secret-keys-to-specific-paths

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncercustomtlssecretitemsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.customTLSSecret.items[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncercustomtlssecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecproxypgbouncerexpose">
  PerconaPGCluster.spec.proxy.pgBouncer.expose
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



Specification of the service that exposes PgBouncer.

|                 | |
|-----------------|-|
| **Key**         | annotations |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | labels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | nodePort |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The port on which this service is exposed when type is NodePort or LoadBalancer. Value must be in-range and not in use or the operation will fail. If unspecified, a port will be allocated if this Service requires one. - https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport |
| | |
| **Key**         | type |
| **Value**       | enum |
| **Required**    | false |
| **Example**     | |
| **Description** | More info: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types |
| | |



<h3 id="perconapgclusterspecproxypgbouncermetadata">
  PerconaPGCluster.spec.proxy.pgBouncer.metadata
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



Metadata contains metadata for PostgresCluster resources

|                 | |
|-----------------|-|
| **Key**         | annotations |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | labels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterspecproxypgbouncerresources">
  PerconaPGCluster.spec.proxy.pgBouncer.resources
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



Compute resources of a PgBouncer container. Changing this value causes PgBouncer to restart. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



A single application container that you want to run within a pod.

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name of the container specified as a DNS_LABEL. Each container in a pod must have a unique name (DNS_LABEL). Cannot be updated. |
| | |
| **Key**         | args |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Arguments to the entrypoint. The container image's CMD is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container's environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. "$$(VAR_NAME)" will produce the string literal "$(VAR_NAME)". Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell |
| | |
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Entrypoint array. Not executed within a shell. The container image's ENTRYPOINT is used if this is not provided. Variable references $(VAR_NAME) are expanded using the container's environment. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. "$$(VAR_NAME)" will produce the string literal "$(VAR_NAME)". Escaped references will never be expanded, regardless of whether the variable exists or not. Cannot be updated. More info: https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/#running-a-command-in-a-shell |
| | |
| **Key**         | env |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | List of environment variables to set in the container. Cannot be updated. |
| | |
| **Key**         | envFrom |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | List of sources to populate environment variables in the container. The keys defined within a source must be a C_IDENTIFIER. All invalid keys will be reported as an event when the container is starting. When a key exists in multiple sources, the value associated with the last source will take precedence. Values defined by an Env with a duplicate key will take precedence. Cannot be updated. |
| | |
| **Key**         | image |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container image name. More info: https://kubernetes.io/docs/concepts/containers/images This field is optional to allow higher level config management to default or override container images in workload controllers like Deployments and StatefulSets. |
| | |
| **Key**         | imagePullPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Image pull policy. One of Always, Never, IfNotPresent. Defaults to Always if :latest tag is specified, or IfNotPresent otherwise. Cannot be updated. More info: https://kubernetes.io/docs/concepts/containers/images#updating-images |
| | |
| **Key**         | lifecycle |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Actions that the management system should take in response to container lifecycle events. Cannot be updated. |
| | |
| **Key**         | livenessProbe |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | ports |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | List of ports to expose from the container. Not specifying a port here DOES NOT prevent that port from being exposed. Any port which is listening on the default "0.0.0.0" address inside a container will be accessible from the network. Modifying this array with strategic merge patch may corrupt the data. For more information See https://github.com/kubernetes/kubernetes/issues/108255. Cannot be updated. |
| | |
| **Key**         | readinessProbe |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | resources |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | securityContext |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/ |
| | |
| **Key**         | startupProbe |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod's lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | stdin |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container should allocate a buffer for stdin in the container runtime. If this is not set, reads from stdin in the container will always result in EOF. Default is false. |
| | |
| **Key**         | stdinOnce |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether the container runtime should close the stdin channel after it has been opened by a single attach. When stdin is true the stdin stream will remain open across multiple attach sessions. If stdinOnce is set to true, stdin is opened on container start, is empty until the first client attaches to stdin, and then remains open and accepts data until the client disconnects, at which time stdin is closed and remains closed until the container is restarted. If this flag is false, a container processes that reads from stdin will never receive an EOF. Default is false |
| | |
| **Key**         | terminationMessagePath |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Path at which the file to which the container's termination message will be written is mounted into the container's filesystem. Message written is intended to be brief final status, such as an assertion failure message. Will be truncated by the node if greater than 4096 bytes. The total message length across all containers will be limited to 12kb. Defaults to /dev/termination-log. Cannot be updated. |
| | |
| **Key**         | terminationMessagePolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Indicate how the termination message should be populated. File will use the contents of terminationMessagePath to populate the container status message on both success and failure. FallbackToLogsOnError will use the last chunk of container log output if the termination message file is empty and the container exited with an error. The log output is limited to 2048 bytes or 80 lines, whichever is smaller. Defaults to File. Cannot be updated. |
| | |
| **Key**         | tty |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container should allocate a TTY for itself, also requires 'stdin' to be true. Default is false. |
| | |
| **Key**         | volumeDevices |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | volumeDevices is the list of block devices to be used by the container. |
| | |
| **Key**         | volumeMounts |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Pod volumes to mount into the container's filesystem. Cannot be updated. |
| | |
| **Key**         | workingDir |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container's working directory. If not specified, the container runtime's default will be used, which might be configured in the container image. Cannot be updated. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].env[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



EnvVar represents an environment variable present in a Container.

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name of the environment variable. Must be a C_IDENTIFIER. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Variable references $(VAR_NAME) are expanded using the previously defined environment variables in the container and any service environment variables. If a variable cannot be resolved, the reference in the input string will be unchanged. Double $$ are reduced to a single $, which allows for escaping the $(VAR_NAME) syntax: i.e. "$$(VAR_NAME)" will produce the string literal "$(VAR_NAME)". Escaped references will never be expanded, regardless of whether the variable exists or not. Defaults to "". |
| | |
| **Key**         | valueFrom |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Source for the environment variable's value. Cannot be used if value is not empty. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefrom">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].env[index].valueFrom
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvindex">↩ Parent</a></sup></sup>
</h3>



Source for the environment variable's value. Cannot be used if value is not empty.

|                 | |
|-----------------|-|
| **Key**         | configMapKeyRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a key of a ConfigMap. |
| | |
| **Key**         | fieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels['<KEY>']`, `metadata.annotations['<KEY>']`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs. |
| | |
| **Key**         | resourceFieldRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported. |
| | |
| **Key**         | secretKeyRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Selects a key of a secret in the pod's namespace |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefromconfigmapkeyref">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].env[index].valueFrom.configMapKeyRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a key of a ConfigMap.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The key to select. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the ConfigMap or its key must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefromfieldref">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].env[index].valueFrom.fieldRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a field of the pod: supports metadata.name, metadata.namespace, `metadata.labels['<KEY>']`, `metadata.annotations['<KEY>']`, spec.nodeName, spec.serviceAccountName, status.hostIP, status.podIP, status.podIPs.

|                 | |
|-----------------|-|
| **Key**         | fieldPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path of the field to select in the specified API version. |
| | |
| **Key**         | apiVersion |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Version of the schema the FieldPath is written in terms of, defaults to "v1". |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefromresourcefieldref">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].env[index].valueFrom.resourceFieldRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a resource of the container: only resources limits and requests (limits.cpu, limits.memory, limits.ephemeral-storage, requests.cpu, requests.memory and requests.ephemeral-storage) are currently supported.

|                 | |
|-----------------|-|
| **Key**         | resource |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Required: resource to select |
| | |
| **Key**         | containerName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Container name: required for volumes, optional for env vars |
| | |
| **Key**         | divisor |
| **Value**       | int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies the output format of the exposed resources, defaults to "1" |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefromsecretkeyref">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].env[index].valueFrom.secretKeyRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvindexvaluefrom">↩ Parent</a></sup></sup>
</h3>



Selects a key of a secret in the pod's namespace

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The key of the secret to select from.  Must be a valid secret key. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvfromindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].envFrom[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



EnvFromSource represents the source of a set of ConfigMaps

|                 | |
|-----------------|-|
| **Key**         | configMapRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The ConfigMap to select from |
| | |
| **Key**         | prefix |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | An optional identifier to prepend to each key in the ConfigMap. Must be a C_IDENTIFIER. |
| | |
| **Key**         | secretRef |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The Secret to select from |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvfromindexconfigmapref">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].envFrom[index].configMapRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvfromindex">↩ Parent</a></sup></sup>
</h3>



The ConfigMap to select from

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the ConfigMap must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexenvfromindexsecretref">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].envFrom[index].secretRef
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexenvfromindex">↩ Parent</a></sup></sup>
</h3>



The Secret to select from

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specify whether the Secret must be defined |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecycle">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



Actions that the management system should take in response to container lifecycle events. Cannot be updated.

|                 | |
|-----------------|-|
| **Key**         | postStart |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks |
| | |
| **Key**         | preStop |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod's termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod's termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststart">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.postStart
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecycle">↩ Parent</a></sup></sup>
</h3>



PostStart is called immediately after a container is created. If the handler fails, the container is terminated and restarted according to its restart policy. Other management of the container blocks until the hook completes. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststartexec">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.postStart.exec
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststart">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststarthttpget">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.postStart.httpGet
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststart">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststarthttpgethttpheadersindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.postStart.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststarthttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststarttcpsocket">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.postStart.tcpSocket
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecyclepoststart">↩ Parent</a></sup></sup>
</h3>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestop">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.preStop
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecycle">↩ Parent</a></sup></sup>
</h3>



PreStop is called immediately before a container is terminated due to an API request or management event such as liveness/startup probe failure, preemption, resource contention, etc. The handler is not called if the container crashes or exits. The Pod's termination grace period countdown begins before the PreStop hook is executed. Regardless of the outcome of the handler, the container will eventually terminate within the Pod's termination grace period (unless delayed by finalizers). Other management of the container blocks until the hook completes or until the termination grace period is reached. More info: https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#container-hooks

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestopexec">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.preStop.exec
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestop">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestophttpget">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.preStop.httpGet
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestop">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestophttpgethttpheadersindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.preStop.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestophttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestoptcpsocket">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].lifecycle.preStop.tcpSocket
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlifecycleprestop">↩ Parent</a></sup></sup>
</h3>



Deprecated. TCPSocket is NOT supported as a LifecycleHandler and kept for the backward compatibility. There are no validation of this field and lifecycle hooks will fail in runtime when tcp handler is specified.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlivenessprobe">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].livenessProbe
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



Periodic probe of container liveness. Container will be restarted if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | failureThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1. |
| | |
| **Key**         | grpc |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | initialDelaySeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | periodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1. |
| | |
| **Key**         | successThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | TCPSocket specifies an action involving a TCP port. |
| | |
| **Key**         | terminationGracePeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod's terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset. |
| | |
| **Key**         | timeoutSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlivenessprobeexec">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].livenessProbe.exec
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlivenessprobegrpc">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].livenessProbe.grpc
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Port number of the gRPC service. Number must be in the range 1 to 65535. |
| | |
| **Key**         | service |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlivenessprobehttpget">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].livenessProbe.httpGet
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlivenessprobehttpgethttpheadersindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].livenessProbe.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlivenessprobehttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexlivenessprobetcpsocket">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].livenessProbe.tcpSocket
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexlivenessprobe">↩ Parent</a></sup></sup>
</h3>



TCPSocket specifies an action involving a TCP port.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexportsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].ports[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



ContainerPort represents a network port in a single container.

|                 | |
|-----------------|-|
| **Key**         | containerPort |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Number of port to expose on the pod's IP address. This must be a valid port number, 0 < x < 65536. |
| | |
| **Key**         | hostIP |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | What host IP to bind the external port to. |
| | |
| **Key**         | hostPort |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of port to expose on the host. If specified, this must be a valid port number, 0 < x < 65536. If HostNetwork is specified, this must match ContainerPort. Most containers do not need this. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | If specified, this must be an IANA_SVC_NAME and unique within the pod. Each named port in a pod must have a unique name. Name for the port that can be referred to by services. |
| | |
| **Key**         | protocol |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Protocol for port. Must be UDP, TCP, or SCTP. Defaults to "TCP". |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexreadinessprobe">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].readinessProbe
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



Periodic probe of container service readiness. Container will be removed from service endpoints if the probe fails. Cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | failureThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1. |
| | |
| **Key**         | grpc |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | initialDelaySeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | periodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1. |
| | |
| **Key**         | successThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | TCPSocket specifies an action involving a TCP port. |
| | |
| **Key**         | terminationGracePeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod's terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset. |
| | |
| **Key**         | timeoutSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexreadinessprobeexec">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].readinessProbe.exec
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexreadinessprobegrpc">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].readinessProbe.grpc
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Port number of the gRPC service. Number must be in the range 1 to 65535. |
| | |
| **Key**         | service |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexreadinessprobehttpget">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].readinessProbe.httpGet
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexreadinessprobehttpgethttpheadersindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].readinessProbe.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexreadinessprobehttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexreadinessprobetcpsocket">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].readinessProbe.tcpSocket
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexreadinessprobe">↩ Parent</a></sup></sup>
</h3>



TCPSocket specifies an action involving a TCP port.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexresources">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].resources
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



Compute Resources required by this container. Cannot be updated. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/

|                 | |
|-----------------|-|
| **Key**         | limits |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Limits describes the maximum amount of compute resources allowed. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |
| **Key**         | requests |
| **Value**       | map[string]int or string |
| **Required**    | false |
| **Example**     | |
| **Description** | Requests describes the minimum amount of compute resources required. If Requests is omitted for a container, it defaults to Limits if that is explicitly specified, otherwise to an implementation-defined value. More info: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/ |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexsecuritycontext">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].securityContext
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



SecurityContext defines the security options the container should be run with. If set, the fields of SecurityContext override the equivalent fields of PodSecurityContext. More info: https://kubernetes.io/docs/tasks/configure-pod-container/security-context/

|                 | |
|-----------------|-|
| **Key**         | allowPrivilegeEscalation |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | AllowPrivilegeEscalation controls whether a process can gain more privileges than its parent process. This bool directly controls if the no_new_privs flag will be set on the container process. AllowPrivilegeEscalation is true always when the container is: 1) run as Privileged 2) has CAP_SYS_ADMIN Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | capabilities |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | privileged |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Run container in privileged mode. Processes in privileged containers are essentially equivalent to root on the host. Defaults to false. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | procMount |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | procMount denotes the type of proc mount to use for the containers. The default is DefaultProcMount which uses the container runtime defaults for readonly paths and masked paths. This requires the ProcMountType feature flag to be enabled. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | readOnlyRootFilesystem |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether this container has a read-only root filesystem. Default is false. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | runAsGroup |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The GID to run the entrypoint of the container process. Uses runtime default if unset. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | runAsNonRoot |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Indicates that the container must run as a non-root user. If true, the Kubelet will validate the image at runtime to ensure that it does not run as UID 0 (root) and fail to start the container if it does. If unset or false, no such validation will be performed. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. |
| | |
| **Key**         | runAsUser |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The UID to run the entrypoint of the container process. Defaults to user specified in image metadata if unspecified. May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | seLinuxOptions |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | seccompProfile |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The seccomp options to use by this container. If seccomp options are provided at both the pod & container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows. |
| | |
| **Key**         | windowsOptions |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexsecuritycontextcapabilities">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].securityContext.capabilities
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The capabilities to add/drop when running containers. Defaults to the default set of capabilities granted by the container runtime. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | add |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Added capabilities |
| | |
| **Key**         | drop |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Removed capabilities |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexsecuritycontextselinuxoptions">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].securityContext.seLinuxOptions
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The SELinux context to be applied to the container. If unspecified, the container runtime will allocate a random SELinux context for each container.  May also be set in PodSecurityContext.  If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | level |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Level is SELinux level label that applies to the container. |
| | |
| **Key**         | role |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Role is a SELinux role label that applies to the container. |
| | |
| **Key**         | type |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Type is a SELinux type label that applies to the container. |
| | |
| **Key**         | user |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | User is a SELinux user label that applies to the container. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexsecuritycontextseccompprofile">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].securityContext.seccompProfile
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The seccomp options to use by this container. If seccomp options are provided at both the pod & container level, the container options override the pod options. Note that this field cannot be set when spec.os.name is windows.

|                 | |
|-----------------|-|
| **Key**         | type |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | type indicates which kind of seccomp profile will be applied. Valid options are: 
 Localhost - a profile defined in a file on the node should be used. RuntimeDefault - the container runtime default profile should be used. Unconfined - no profile should be applied. |
| | |
| **Key**         | localhostProfile |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | localhostProfile indicates a profile defined in a file on the node should be used. The profile must be preconfigured on the node to work. Must be a descending path, relative to the kubelet's configured seccomp profile location. Must only be set if type is "Localhost". |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexsecuritycontextwindowsoptions">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].securityContext.windowsOptions
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexsecuritycontext">↩ Parent</a></sup></sup>
</h3>



The Windows specific settings applied to all containers. If unspecified, the options from the PodSecurityContext will be used. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. Note that this field cannot be set when spec.os.name is linux.

|                 | |
|-----------------|-|
| **Key**         | gmsaCredentialSpec |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | GMSACredentialSpec is where the GMSA admission webhook (https://github.com/kubernetes-sigs/windows-gmsa) inlines the contents of the GMSA credential spec named by the GMSACredentialSpecName field. |
| | |
| **Key**         | gmsaCredentialSpecName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | GMSACredentialSpecName is the name of the GMSA credential spec to use. |
| | |
| **Key**         | hostProcess |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | HostProcess determines if a container should be run as a 'Host Process' container. This field is alpha-level and will only be honored by components that enable the WindowsHostProcessContainers feature flag. Setting this field without the feature flag will result in errors when validating the Pod. All of a Pod's containers must have the same effective HostProcess value (it is not allowed to have a mix of HostProcess containers and non-HostProcess containers).  In addition, if HostProcess is true then HostNetwork must also be set to true. |
| | |
| **Key**         | runAsUserName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The UserName in Windows to run the entrypoint of the container process. Defaults to the user specified in image metadata if unspecified. May also be set in PodSecurityContext. If set in both SecurityContext and PodSecurityContext, the value specified in SecurityContext takes precedence. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexstartupprobe">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].startupProbe
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



StartupProbe indicates that the Pod has successfully initialized. If specified, no other probes are executed until this completes successfully. If this probe fails, the Pod will be restarted, just as if the livenessProbe failed. This can be used to provide different probe parameters at the beginning of a Pod's lifecycle, when it might take a long time to load data or warm a cache, than during steady-state operation. This cannot be updated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes

|                 | |
|-----------------|-|
| **Key**         | exec |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Exec specifies the action to take. |
| | |
| **Key**         | failureThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive failures for the probe to be considered failed after having succeeded. Defaults to 3. Minimum value is 1. |
| | |
| **Key**         | grpc |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate. |
| | |
| **Key**         | httpGet |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | HTTPGet specifies the http request to perform. |
| | |
| **Key**         | initialDelaySeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after the container has started before liveness probes are initiated. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |
| **Key**         | periodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | How often (in seconds) to perform the probe. Default to 10 seconds. Minimum value is 1. |
| | |
| **Key**         | successThreshold |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Minimum consecutive successes for the probe to be considered successful after having failed. Defaults to 1. Must be 1 for liveness and startup. Minimum value is 1. |
| | |
| **Key**         | tcpSocket |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | TCPSocket specifies an action involving a TCP port. |
| | |
| **Key**         | terminationGracePeriodSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional duration in seconds the pod needs to terminate gracefully upon probe failure. The grace period is the duration in seconds after the processes running in the pod are sent a termination signal and the time when the processes are forcibly halted with a kill signal. Set this value longer than the expected cleanup time for your process. If this value is nil, the pod's terminationGracePeriodSeconds will be used. Otherwise, this value overrides the value provided by the pod spec. Value must be non-negative integer. The value zero indicates stop immediately via the kill signal (no opportunity to shut down). This is a beta field and requires enabling ProbeTerminationGracePeriod feature gate. Minimum value is 1. spec.terminationGracePeriodSeconds is used if unset. |
| | |
| **Key**         | timeoutSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Number of seconds after which the probe times out. Defaults to 1 second. Minimum value is 1. More info: https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle#container-probes |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexstartupprobeexec">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].startupProbe.exec
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



Exec specifies the action to take.

|                 | |
|-----------------|-|
| **Key**         | command |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command is the command line to execute inside the container, the working directory for the command  is root ('/') in the container's filesystem. The command is simply exec'd, it is not run inside a shell, so traditional shell instructions ('|', etc) won't work. To use a shell, you need to explicitly call out to that shell. Exit status of 0 is treated as live/healthy and non-zero is unhealthy. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexstartupprobegrpc">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].startupProbe.grpc
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



GRPC specifies an action involving a GRPC port. This is a beta field and requires enabling GRPCContainerProbe feature gate.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | Port number of the gRPC service. Number must be in the range 1 to 65535. |
| | |
| **Key**         | service |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Service is the name of the service to place in the gRPC HealthCheckRequest (see https://github.com/grpc/grpc/blob/master/doc/health-checking.md). 
 If this is not specified, the default behavior is defined by gRPC. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexstartupprobehttpget">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].startupProbe.httpGet
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



HTTPGet specifies the http request to perform.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Name or number of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Host name to connect to, defaults to the pod IP. You probably want to set "Host" in httpHeaders instead. |
| | |
| **Key**         | httpHeaders |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Custom headers to set in the request. HTTP allows repeated headers. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path to access on the HTTP server. |
| | |
| **Key**         | scheme |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Scheme to use for connecting to the host. Defaults to HTTP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexstartupprobehttpgethttpheadersindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].startupProbe.httpGet.httpHeaders[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexstartupprobehttpget">↩ Parent</a></sup></sup>
</h3>



HTTPHeader describes a custom header to be used in HTTP probes

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field name |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The header field value |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexstartupprobetcpsocket">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].startupProbe.tcpSocket
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindexstartupprobe">↩ Parent</a></sup></sup>
</h3>



TCPSocket specifies an action involving a TCP port.

|                 | |
|-----------------|-|
| **Key**         | port |
| **Value**       | int or string |
| **Required**    | true |
| **Example**     | |
| **Description** | Number or name of the port to access on the container. Number must be in the range 1 to 65535. Name must be an IANA_SVC_NAME. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Optional: Host name to connect to, defaults to the pod IP. |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexvolumedevicesindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].volumeDevices[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



volumeDevice describes a mapping of a raw block device within a container.

|                 | |
|-----------------|-|
| **Key**         | devicePath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | devicePath is the path inside of the container that the device will be mapped to. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | name must match the name of a persistentVolumeClaim in the pod |
| | |



<h3 id="perconapgclusterspecproxypgbouncersidecarsindexvolumemountsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.sidecars[index].volumeMounts[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncersidecarsindex">↩ Parent</a></sup></sup>
</h3>



VolumeMount describes a mounting of a Volume within a container.

|                 | |
|-----------------|-|
| **Key**         | mountPath |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | Path within the container at which the volume should be mounted.  Must not contain ':'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | This must match the Name of a Volume. |
| | |
| **Key**         | mountPropagation |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | mountPropagation determines how mounts are propagated from the host to container and the other way around. When not set, MountPropagationNone is used. This field is beta in 1.10. |
| | |
| **Key**         | readOnly |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Mounted read-only if true, read-write otherwise (false or unspecified). Defaults to false. |
| | |
| **Key**         | subPath |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Path within the volume from which the container's volume should be mounted. Defaults to "" (volume's root). |
| | |
| **Key**         | subPathExpr |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Expanded path within the volume from which the container's volume should be mounted. Behaves similarly to SubPath but environment variable references $(VAR_NAME) are expanded using the container's environment. Defaults to "" (volume's root). SubPathExpr and SubPath are mutually exclusive. |
| | |



<h3 id="perconapgclusterspecproxypgbouncertolerationsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.tolerations[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



The pod this Toleration is attached to tolerates any taint that matches the triple <key,value,effect> using the matching operator <operator>.

|                 | |
|-----------------|-|
| **Key**         | effect |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Effect indicates the taint effect to match. Empty means match all taint effects. When specified, allowed values are NoSchedule, PreferNoSchedule and NoExecute. |
| | |
| **Key**         | key |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Key is the taint key that the toleration applies to. Empty means match all taint keys. If the key is empty, operator must be Exists; this combination means to match all values and all keys. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Operator represents a key's relationship to the value. Valid operators are Exists and Equal. Defaults to Equal. Exists is equivalent to wildcard for value, so that a pod can tolerate all taints of a particular category. |
| | |
| **Key**         | tolerationSeconds |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | TolerationSeconds represents the period of time the toleration (which must be of effect NoExecute, otherwise this field is ignored) tolerates the taint. By default, it is not set, which means tolerate the taint forever (do not evict). Zero and negative values will be treated as 0 (evict immediately) by the system. |
| | |
| **Key**         | value |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Value is the taint value the toleration matches to. If the operator is Exists, the value should be empty, otherwise just a regular string. |
| | |



<h3 id="perconapgclusterspecproxypgbouncertopologyspreadconstraintsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.topologySpreadConstraints[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncer">↩ Parent</a></sup></sup>
</h3>



TopologySpreadConstraint specifies how to spread matching pods among the given topology.

|                 | |
|-----------------|-|
| **Key**         | maxSkew |
| **Value**       | integer |
| **Required**    | true |
| **Example**     | |
| **Description** | MaxSkew describes the degree to which pods may be unevenly distributed. When `whenUnsatisfiable=DoNotSchedule`, it is the maximum permitted difference between the number of matching pods in the target topology and the global minimum. The global minimum is the minimum number of matching pods in an eligible domain or zero if the number of eligible domains is less than MinDomains. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 2/2/1: In this case, the global minimum is 1. | zone1 | zone2 | zone3 | |  P P  |  P P  |   P   | - if MaxSkew is 1, incoming pod can only be scheduled to zone3 to become 2/2/2; scheduling it onto zone1(zone2) would make the ActualSkew(3-1) on zone1(zone2) violate MaxSkew(1). - if MaxSkew is 2, incoming pod can be scheduled onto any zone. When `whenUnsatisfiable=ScheduleAnyway`, it is used to give higher precedence to topologies that satisfy it. It's a required field. Default value is 1 and 0 is not allowed. |
| | |
| **Key**         | topologyKey |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | TopologyKey is the key of node labels. Nodes that have a label with this key and identical values are considered to be in the same topology. We consider each <key, value> as a "bucket", and try to put balanced number of pods into each bucket. We define a domain as a particular instance of a topology. Also, we define an eligible domain as a domain whose nodes meet the requirements of nodeAffinityPolicy and nodeTaintsPolicy. e.g. If TopologyKey is "kubernetes.io/hostname", each Node is a domain of that topology. And, if TopologyKey is "topology.kubernetes.io/zone", each zone is a domain of that topology. It's a required field. |
| | |
| **Key**         | whenUnsatisfiable |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | WhenUnsatisfiable indicates how to deal with a pod if it doesn't satisfy the spread constraint. - DoNotSchedule (default) tells the scheduler not to schedule it. - ScheduleAnyway tells the scheduler to schedule the pod in any location, but giving higher precedence to topologies that would help reduce the skew. A constraint is considered "Unsatisfiable" for an incoming pod if and only if every possible node assignment for that pod would violate "MaxSkew" on some topology. For example, in a 3-zone cluster, MaxSkew is set to 1, and pods with the same labelSelector spread as 3/1/1: | zone1 | zone2 | zone3 | | P P P |   P   |   P   | If WhenUnsatisfiable is set to DoNotSchedule, incoming pod can only be scheduled to zone2(zone3) to become 3/2/1(3/1/2) as ActualSkew(2-1) on zone2(zone3) satisfies MaxSkew(1). In other words, the cluster can still be imbalanced, but scheduler won't make it *more* imbalanced. It's a required field. |
| | |
| **Key**         | labelSelector |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain. |
| | |
| **Key**         | matchLabelKeys |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | MatchLabelKeys is a set of pod label keys to select the pods over which spreading will be calculated. The keys are used to lookup values from the incoming pod labels, those key-value labels are ANDed with labelSelector to select the group of existing pods over which spreading will be calculated for the incoming pod. Keys that don't exist in the incoming pod labels will be ignored. A null or empty list means only match against labelSelector. |
| | |
| **Key**         | minDomains |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | MinDomains indicates a minimum number of eligible domains. When the number of eligible domains with matching topology keys is less than minDomains, Pod Topology Spread treats "global minimum" as 0, and then the calculation of Skew is performed. And when the number of eligible domains with matching topology keys equals or greater than minDomains, this value has no effect on scheduling. As a result, when the number of eligible domains is less than minDomains, scheduler won't schedule more than maxSkew Pods to those domains. If value is nil, the constraint behaves as if MinDomains is equal to 1. Valid values are integers greater than 0. When value is not nil, WhenUnsatisfiable must be DoNotSchedule. 
 For example, in a 3-zone cluster, MaxSkew is set to 2, MinDomains is set to 5 and pods with the same labelSelector spread as 2/2/2: | zone1 | zone2 | zone3 | |  P P  |  P P  |  P P  | The number of domains is less than 5(MinDomains), so "global minimum" is treated as 0. In this situation, new pod with the same labelSelector cannot be scheduled, because computed skew will be 3(3 - 0) if new Pod is scheduled to any of the three zones, it will violate MaxSkew. 
 This is a beta field and requires the MinDomainsInPodTopologySpread feature gate to be enabled (enabled by default). |
| | |
| **Key**         | nodeAffinityPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | NodeAffinityPolicy indicates how we will treat Pod's nodeAffinity/nodeSelector when calculating pod topology spread skew. Options are: - Honor: only nodes matching nodeAffinity/nodeSelector are included in the calculations. - Ignore: nodeAffinity/nodeSelector are ignored. All nodes are included in the calculations. 
 If this value is nil, the behavior is equivalent to the Honor policy. This is a alpha-level feature enabled by the NodeInclusionPolicyInPodTopologySpread feature flag. |
| | |
| **Key**         | nodeTaintsPolicy |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | NodeTaintsPolicy indicates how we will treat node taints when calculating pod topology spread skew. Options are: - Honor: nodes without taints, along with tainted nodes for which the incoming pod has a toleration, are included. - Ignore: node taints are ignored. All nodes are included. 
 If this value is nil, the behavior is equivalent to the Ignore policy. This is a alpha-level feature enabled by the NodeInclusionPolicyInPodTopologySpread feature flag. |
| | |



<h3 id="perconapgclusterspecproxypgbouncertopologyspreadconstraintsindexlabelselector">
  PerconaPGCluster.spec.proxy.pgBouncer.topologySpreadConstraints[index].labelSelector
  <sup><sup><a href="#perconapgclusterspecproxypgbouncertopologyspreadconstraintsindex">↩ Parent</a></sup></sup>
</h3>



LabelSelector is used to find matching pods. Pods that match this label selector are counted to determine the number of pods in their corresponding topology domain.

|                 | |
|-----------------|-|
| **Key**         | matchExpressions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | matchExpressions is a list of label selector requirements. The requirements are ANDed. |
| | |
| **Key**         | matchLabels |
| **Value**       | map[string]string |
| **Required**    | false |
| **Example**     | |
| **Description** | matchLabels is a map of {key,value} pairs. A single {key,value} in the matchLabels map is equivalent to an element of matchExpressions, whose key field is "key", the operator is "In", and the values array contains only "value". The requirements are ANDed. |
| | |



<h3 id="perconapgclusterspecproxypgbouncertopologyspreadconstraintsindexlabelselectormatchexpressionsindex">
  PerconaPGCluster.spec.proxy.pgBouncer.topologySpreadConstraints[index].labelSelector.matchExpressions[index]
  <sup><sup><a href="#perconapgclusterspecproxypgbouncertopologyspreadconstraintsindexlabelselector">↩ Parent</a></sup></sup>
</h3>



A label selector requirement is a selector that contains values, a key, and an operator that relates the key and values.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the label key that the selector applies to. |
| | |
| **Key**         | operator |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | operator represents a key's relationship to a set of values. Valid operators are In, NotIn, Exists and DoesNotExist. |
| | |
| **Key**         | values |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | values is an array of string values. If the operator is In or NotIn, the values array must be non-empty. If the operator is Exists or DoesNotExist, the values array must be empty. This array is replaced during a strategic merge patch. |
| | |



<h3 id="perconapgclusterspecsecrets">
  PerconaPGCluster.spec.secrets
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | customReplicationTLSSecret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The secret containing the replication client certificates and keys for secure connections to the PostgreSQL server. It will need to contain the client TLS certificate, TLS key and the Certificate Authority certificate with the data keys set to tls.crt, tls.key and ca.crt, respectively. NOTE: If CustomReplicationClientTLSSecret is provided, CustomTLSSecret MUST be provided and the ca.crt provided must be the same. |
| | |
| **Key**         | customTLSSecret |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The secret containing the Certificates and Keys to encrypt PostgreSQL traffic will need to contain the server TLS certificate, TLS key and the Certificate Authority certificate with the data keys set to tls.crt, tls.key and ca.crt, respectively. It will then be mounted as a volume projection to the '/pgconf/tls' directory. For more information on Kubernetes secret projections, please see https://k8s.io/docs/concepts/configuration/secret/#projection-of-secret-keys-to-specific-paths NOTE: If CustomTLSSecret is provided, CustomReplicationClientTLSSecret MUST be provided and the ca.crt provided must be the same. |
| | |



<h3 id="perconapgclusterspecsecretscustomreplicationtlssecret">
  PerconaPGCluster.spec.secrets.customReplicationTLSSecret
  <sup><sup><a href="#perconapgclusterspecsecrets">↩ Parent</a></sup></sup>
</h3>



The secret containing the replication client certificates and keys for secure connections to the PostgreSQL server. It will need to contain the client TLS certificate, TLS key and the Certificate Authority certificate with the data keys set to tls.crt, tls.key and ca.crt, respectively. NOTE: If CustomReplicationClientTLSSecret is provided, CustomTLSSecret MUST be provided and the ca.crt provided must be the same.

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecsecretscustomreplicationtlssecretitemsindex">
  PerconaPGCluster.spec.secrets.customReplicationTLSSecret.items[index]
  <sup><sup><a href="#perconapgclusterspecsecretscustomreplicationtlssecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecsecretscustomtlssecret">
  PerconaPGCluster.spec.secrets.customTLSSecret
  <sup><sup><a href="#perconapgclusterspecsecrets">↩ Parent</a></sup></sup>
</h3>



The secret containing the Certificates and Keys to encrypt PostgreSQL traffic will need to contain the server TLS certificate, TLS key and the Certificate Authority certificate with the data keys set to tls.crt, tls.key and ca.crt, respectively. It will then be mounted as a volume projection to the '/pgconf/tls' directory. For more information on Kubernetes secret projections, please see https://k8s.io/docs/concepts/configuration/secret/#projection-of-secret-keys-to-specific-paths NOTE: If CustomTLSSecret is provided, CustomReplicationClientTLSSecret MUST be provided and the ca.crt provided must be the same.

|                 | |
|-----------------|-|
| **Key**         | items |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | items if unspecified, each key-value pair in the Data field of the referenced Secret will be projected into the volume as a file whose name is the key and content is the value. If specified, the listed keys will be projected into the specified paths, and unlisted keys will not be present. If a key is specified which is not present in the Secret, the volume setup will error unless it is marked optional. Paths must be relative and may not contain the '..' path or start with '..'. |
| | |
| **Key**         | name |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Name of the referent. More info: https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names TODO: Add other useful fields. apiVersion, kind, uid? |
| | |
| **Key**         | optional |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | optional field specify whether the Secret or its key must be defined |
| | |



<h3 id="perconapgclusterspecsecretscustomtlssecretitemsindex">
  PerconaPGCluster.spec.secrets.customTLSSecret.items[index]
  <sup><sup><a href="#perconapgclusterspecsecretscustomtlssecret">↩ Parent</a></sup></sup>
</h3>



Maps a string key to a path within a volume.

|                 | |
|-----------------|-|
| **Key**         | key |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | key is the key to project. |
| | |
| **Key**         | path |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | path is the relative path of the file to map the key to. May not be an absolute path. May not contain the path element '..'. May not start with the string '..'. |
| | |
| **Key**         | mode |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | mode is Optional: mode bits used to set permissions on this file. Must be an octal value between 0000 and 0777 or a decimal value between 0 and 511. YAML accepts both octal and decimal values, JSON requires decimal values for mode bits. If not specified, the volume defaultMode will be used. This might be in conflict with other options that affect the file mode, like fsGroup, and the result can be other mode bits set. |
| | |



<h3 id="perconapgclusterspecstandby">
  PerconaPGCluster.spec.standby
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>



Run this cluster as a read-only copy of an existing cluster or archive.

|                 | |
|-----------------|-|
| **Key**         | enabled |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether or not the PostgreSQL cluster should be read-only. When this is true, WAL files are applied from a pgBackRest repository or another PostgreSQL server. |
| | |
| **Key**         | host |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Network address of the PostgreSQL server to follow via streaming replication. |
| | |
| **Key**         | port |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Network port of the PostgreSQL server to follow via streaming replication. |
| | |
| **Key**         | repoName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The name of the pgBackRest repository to follow for WAL files. |
| | |



<h3 id="perconapgclusterspecusersindex">
  PerconaPGCluster.spec.users[index]
  <sup><sup><a href="#perconapgclusterspec">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of this PostgreSQL user. The value may contain only lowercase letters, numbers, and hyphen so that it fits into Kubernetes metadata. |
| | |
| **Key**         | databases |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Databases to which this user can connect and create objects. Removing a database from this list does NOT revoke access. This field is ignored for the "postgres" user. |
| | |
| **Key**         | options |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | ALTER ROLE options except for PASSWORD. This field is ignored for the "postgres" user. More info: https://www.postgresql.org/docs/current/role-attributes.html |
| | |
| **Key**         | password |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Properties of the password generated for this user. |
| | |



<h3 id="perconapgclusterspecusersindexpassword">
  PerconaPGCluster.spec.users[index].password
  <sup><sup><a href="#perconapgclusterspecusersindex">↩ Parent</a></sup></sup>
</h3>



Properties of the password generated for this user.

|                 | |
|-----------------|-|
| **Key**         | type |
| **Value**       | enum |
| **Required**    | true |
| **Example**     | |
| **Description** | Type of password to generate. Defaults to ASCII. Valid options are ASCII and AlphaNumeric. "ASCII" passwords contain letters, numbers, and symbols from the US-ASCII character set. "AlphaNumeric" passwords contain letters and numbers from the US-ASCII character set. |
| | |



<h3 id="perconapgclusterstatus">
  PerconaPGCluster.status
  <sup><sup><a href="#perconapgcluster">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | conditions |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | conditions represent the observations of postgrescluster's current state. Known .status.conditions.type are: "PersistentVolumeResizing", "Progressing", "ProxyAvailable" |
| | |
| **Key**         | databaseInitSQL |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | DatabaseInitSQL state of custom database initialization in the cluster |
| | |
| **Key**         | databaseRevision |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Identifies the databases that have been installed into PostgreSQL. |
| | |
| **Key**         | instances |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Current state of PostgreSQL instances. |
| | |
| **Key**         | monitoring |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Current state of PostgreSQL cluster monitoring tool configuration |
| | |
| **Key**         | observedGeneration |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | observedGeneration represents the .metadata.generation on which the status was based. |
| | |
| **Key**         | patroni |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | pgbackrest |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Status information for pgBackRest |
| | |
| **Key**         | postgresVersion |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Stores the current PostgreSQL major version following a successful major PostgreSQL upgrade. |
| | |
| **Key**         | proxy |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Current state of the PostgreSQL proxy. |
| | |
| **Key**         | startupInstance |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The instance that should be started first when bootstrapping and/or starting a PostgresCluster. |
| | |
| **Key**         | startupInstanceSet |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The instance set associated with the startupInstance |
| | |
| **Key**         | userInterface |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Current state of the PostgreSQL user interface. |
| | |
| **Key**         | usersRevision |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Identifies the users that have been installed into PostgreSQL. |
| | |



<h3 id="perconapgclusterstatusconditionsindex">
  PerconaPGCluster.status.conditions[index]
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>



Condition contains details for one aspect of the current state of this API Resource. --- This struct is intended for direct use as an array at the field path .status.conditions.  For example, 
 type FooStatus struct{ // Represents the observations of a foo's current state. // Known .status.conditions.type are: "Available", "Progressing", and "Degraded" // +patchMergeKey=type // +patchStrategy=merge // +listType=map // +listMapKey=type Conditions []metav1.Condition `json:"conditions,omitempty" patchStrategy:"merge" patchMergeKey:"type" protobuf:"bytes,1,rep,name=conditions"` 
 // other fields }

|                 | |
|-----------------|-|
| **Key**         | lastTransitionTime |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | lastTransitionTime is the last time the condition transitioned from one status to another. This should be when the underlying condition changed.  If that is not known, then using the time when the API field changed is acceptable. |
| | |
| **Key**         | message |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | message is a human readable message indicating details about the transition. This may be an empty string. |
| | |
| **Key**         | reason |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | reason contains a programmatic identifier indicating the reason for the condition's last transition. Producers of specific condition types may define expected values and meanings for this field, and whether the values are considered a guaranteed API. The value should be a CamelCase string. This field may not be empty. |
| | |
| **Key**         | status |
| **Value**       | enum |
| **Required**    | true |
| **Example**     | |
| **Description** | status of the condition, one of True, False, Unknown. |
| | |
| **Key**         | type |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | type of condition in CamelCase or in foo.example.com/CamelCase. --- Many .condition.type values are consistent across resources like Available, but because arbitrary conditions can be useful (see .node.status.conditions), the ability to deconflict is important. The regex it matches is (dns1123SubdomainFmt/)?(qualifiedNameFmt) |
| | |
| **Key**         | observedGeneration |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | observedGeneration represents the .metadata.generation that the condition was set based upon. For instance, if .metadata.generation is currently 12, but the .status.conditions[x].observedGeneration is 9, the condition is out of date with respect to the current state of the instance. |
| | |



<h3 id="perconapgclusterstatusinstancesindex">
  PerconaPGCluster.status.instances[index]
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | readyReplicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Total number of ready pods. |
| | |
| **Key**         | replicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Total number of pods. |
| | |
| **Key**         | updatedReplicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Total number of pods that have the desired specification. |
| | |



<h3 id="perconapgclusterstatusmonitoring">
  PerconaPGCluster.status.monitoring
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>



Current state of PostgreSQL cluster monitoring tool configuration

|                 | |
|-----------------|-|
| **Key**         | exporterConfiguration |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterstatuspatroni">
  PerconaPGCluster.status.patroni
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | switchover |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Tracks the execution of the switchover requests. |
| | |
| **Key**         | switchoverTimeline |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Tracks the current timeline during switchovers |
| | |
| **Key**         | systemIdentifier |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The PostgreSQL system identifier reported by Patroni. |
| | |



<h3 id="perconapgclusterstatuspgbackrest">
  PerconaPGCluster.status.pgbackrest
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>



Status information for pgBackRest

|                 | |
|-----------------|-|
| **Key**         | manualBackup |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Status information for manual backups |
| | |
| **Key**         | repoHost |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Status information for the pgBackRest dedicated repository host |
| | |
| **Key**         | repos |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Status information for pgBackRest repositories |
| | |
| **Key**         | restore |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | Status information for in-place restores |
| | |
| **Key**         | scheduledBackups |
| **Value**       | []object |
| **Required**    | false |
| **Example**     | |
| **Description** | Status information for scheduled backups |
| | |



<h3 id="perconapgclusterstatuspgbackrestmanualbackup">
  PerconaPGCluster.status.pgbackrest.manualBackup
  <sup><sup><a href="#perconapgclusterstatuspgbackrest">↩ Parent</a></sup></sup>
</h3>



Status information for manual backups

|                 | |
|-----------------|-|
| **Key**         | finished |
| **Value**       | boolean |
| **Required**    | true |
| **Example**     | |
| **Description** | Specifies whether or not the Job is finished executing (does not indicate success or failure). |
| | |
| **Key**         | id |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | A unique identifier for the manual backup as provided using the "pgbackrest-backup" annotation when initiating a backup. |
| | |
| **Key**         | active |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of actively running manual backup Pods. |
| | |
| **Key**         | completionTime |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents the time the manual backup Job was determined by the Job controller to be completed.  This field is only set if the backup completed successfully. Additionally, it is represented in RFC3339 form and is in UTC. |
| | |
| **Key**         | failed |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of Pods for the manual backup Job that reached the "Failed" phase. |
| | |
| **Key**         | startTime |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents the time the manual backup Job was acknowledged by the Job controller. It is represented in RFC3339 form and is in UTC. |
| | |
| **Key**         | succeeded |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of Pods for the manual backup Job that reached the "Succeeded" phase. |
| | |



<h3 id="perconapgclusterstatuspgbackrestrepohost">
  PerconaPGCluster.status.pgbackrest.repoHost
  <sup><sup><a href="#perconapgclusterstatuspgbackrest">↩ Parent</a></sup></sup>
</h3>



Status information for the pgBackRest dedicated repository host

|                 | |
|-----------------|-|
| **Key**         | apiVersion |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | APIVersion defines the versioned schema of this representation of an object. Servers should convert recognized schemas to the latest internal value, and may reject unrecognized values. More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources |
| | |
| **Key**         | kind |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds |
| | |
| **Key**         | ready |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether or not the pgBackRest repository host is ready for use |
| | |



<h3 id="perconapgclusterstatuspgbackrestreposindex">
  PerconaPGCluster.status.pgbackrest.repos[index]
  <sup><sup><a href="#perconapgclusterstatuspgbackrest">↩ Parent</a></sup></sup>
</h3>



RepoStatus the status of a pgBackRest repository

|                 | |
|-----------------|-|
| **Key**         | name |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the pgBackRest repository |
| | |
| **Key**         | bound |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Whether or not the pgBackRest repository PersistentVolumeClaim is bound to a volume |
| | |
| **Key**         | replicaCreateBackupComplete |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | ReplicaCreateBackupReady indicates whether a backup exists in the repository as needed to bootstrap replicas. |
| | |
| **Key**         | repoOptionsHash |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | A hash of the required fields in the spec for defining an Azure, GCS or S3 repository, Utilizd to detect changes to these fields and then execute pgBackRest stanza-create commands accordingly. |
| | |
| **Key**         | stanzaCreated |
| **Value**       | boolean |
| **Required**    | false |
| **Example**     | |
| **Description** | Specifies whether or not a stanza has been successfully created for the repository |
| | |
| **Key**         | volume |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The name of the volume the containing the pgBackRest repository |
| | |



<h3 id="perconapgclusterstatuspgbackrestrestore">
  PerconaPGCluster.status.pgbackrest.restore
  <sup><sup><a href="#perconapgclusterstatuspgbackrest">↩ Parent</a></sup></sup>
</h3>



Status information for in-place restores

|                 | |
|-----------------|-|
| **Key**         | finished |
| **Value**       | boolean |
| **Required**    | true |
| **Example**     | |
| **Description** | Specifies whether or not the Job is finished executing (does not indicate success or failure). |
| | |
| **Key**         | id |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | A unique identifier for the manual backup as provided using the "pgbackrest-backup" annotation when initiating a backup. |
| | |
| **Key**         | active |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of actively running manual backup Pods. |
| | |
| **Key**         | completionTime |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents the time the manual backup Job was determined by the Job controller to be completed.  This field is only set if the backup completed successfully. Additionally, it is represented in RFC3339 form and is in UTC. |
| | |
| **Key**         | failed |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of Pods for the manual backup Job that reached the "Failed" phase. |
| | |
| **Key**         | startTime |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents the time the manual backup Job was acknowledged by the Job controller. It is represented in RFC3339 form and is in UTC. |
| | |
| **Key**         | succeeded |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of Pods for the manual backup Job that reached the "Succeeded" phase. |
| | |



<h3 id="perconapgclusterstatuspgbackrestscheduledbackupsindex">
  PerconaPGCluster.status.pgbackrest.scheduledBackups[index]
  <sup><sup><a href="#perconapgclusterstatuspgbackrest">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | active |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of actively running manual backup Pods. |
| | |
| **Key**         | completionTime |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents the time the manual backup Job was determined by the Job controller to be completed.  This field is only set if the backup completed successfully. Additionally, it is represented in RFC3339 form and is in UTC. |
| | |
| **Key**         | cronJobName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The name of the associated pgBackRest scheduled backup CronJob |
| | |
| **Key**         | failed |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of Pods for the manual backup Job that reached the "Failed" phase. |
| | |
| **Key**         | repo |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The name of the associated pgBackRest repository |
| | |
| **Key**         | startTime |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Represents the time the manual backup Job was acknowledged by the Job controller. It is represented in RFC3339 form and is in UTC. |
| | |
| **Key**         | succeeded |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | The number of Pods for the manual backup Job that reached the "Succeeded" phase. |
| | |
| **Key**         | type |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | The pgBackRest backup type for this Job |
| | |



<h3 id="perconapgclusterstatusproxy">
  PerconaPGCluster.status.proxy
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>



Current state of the PostgreSQL proxy.

|                 | |
|-----------------|-|
| **Key**         | pgBouncer |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgclusterstatusproxypgbouncer">
  PerconaPGCluster.status.proxy.pgBouncer
  <sup><sup><a href="#perconapgclusterstatusproxy">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | postgresRevision |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Identifies the revision of PgBouncer assets that have been installed into PostgreSQL. |
| | |
| **Key**         | readyReplicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Total number of ready pods. |
| | |
| **Key**         | replicas |
| **Value**       | integer |
| **Required**    | false |
| **Example**     | |
| **Description** | Total number of non-terminated pods. |
| | |



<h3 id="perconapgclusterstatususerinterface">
  PerconaPGCluster.status.userInterface
  <sup><sup><a href="#perconapgclusterstatus">↩ Parent</a></sup></sup>
</h3>



Current state of the PostgreSQL user interface.

|                 | |
|-----------------|-|
| **Key**         | pgAdmin |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** | The state of the pgAdmin user interface. |
| | |



<h3 id="perconapgclusterstatususerinterfacepgadmin">
  PerconaPGCluster.status.userInterface.pgAdmin
  <sup><sup><a href="#perconapgclusterstatususerinterface">↩ Parent</a></sup></sup>
</h3>



The state of the pgAdmin user interface.

|                 | |
|-----------------|-|
| **Key**         | usersRevision |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** | Hash that indicates which users have been installed into pgAdmin. |
| | |


<h2 id="perconapgbackup">PerconaPGBackup</h2>






PerconaPGBackup is the CRD that defines a Percona PostgreSQL Backup

|                 | |
|-----------------|-|
| **Key**         | spec |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | status |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgbackupspec">
  PerconaPGBackup.spec
  <sup><sup><a href="#perconapgbackup">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | pgCluster |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | repoName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the pgBackRest repo to run the backup command against. |
| | |
| **Key**         | options |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command line options to include when running the pgBackRest backup command. https://pgbackrest.org/command.html#command-backup |
| | |



<h3 id="perconapgbackupstatus">
  PerconaPGBackup.status
  <sup><sup><a href="#perconapgbackup">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | completed |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | jobName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | state |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |


<h2 id="perconapgrestore">PerconaPGRestore</h2>






PerconaPGRestore is the CRD that defines a Percona PostgreSQL Restore

|                 | |
|-----------------|-|
| **Key**         | spec |
| **Value**       | object |
| **Required**    | true |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | status |
| **Value**       | object |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |



<h3 id="perconapgrestorespec">
  PerconaPGRestore.spec
  <sup><sup><a href="#perconapgrestore">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | pgCluster |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the PerconaPGCluster to perform restore. |
| | |
| **Key**         | repoName |
| **Value**       | string |
| **Required**    | true |
| **Example**     | |
| **Description** | The name of the pgBackRest repo within the source PostgresCluster that contains the backups that should be utilized to perform a pgBackRest restore when initializing the data source for the new PostgresCluster. |
| | |
| **Key**         | options |
| **Value**       | []string |
| **Required**    | false |
| **Example**     | |
| **Description** | Command line options to include when running the pgBackRest restore command. https://pgbackrest.org/command.html#command-restore |
| | |



<h3 id="perconapgrestorestatus">
  PerconaPGRestore.status
  <sup><sup><a href="#perconapgrestore">↩ Parent</a></sup></sup>
</h3>





|                 | |
|-----------------|-|
| **Key**         | completed |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | jobName |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |
| **Key**         | state |
| **Value**       | string |
| **Required**    | false |
| **Example**     | |
| **Description** |  |
| | |

