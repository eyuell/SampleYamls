Kubernetes Resource Kind Inclusion Matrix

Resource Kind                   Includes / References                                            Notes
--------------------------------------------------------------------------------------------------------------------------------------------------------------
Deployment	                    Pod (via PodTemplateSpec), ConfigMap, Secret, Volume, PVC        Defines pods to run; references configs, secrets, volumes
DaemonSet	                      Pod (via PodTemplateSpec), ConfigMap, Secret, Volume, PVC        Similar to Deployment but runs one pod per node
StatefulSet	                    Pod, PVC, Headless Service                                       Manages ordered, stateful pods
ReplicaSet	                    PodTemplateSpec                                                  Usually managed by a Deployment
Job	                            Pod                                                              For one-time tasks
CronJob                         Job                                                              Scheduled jobs
Pod                             ConfigMap, Secret, PVC, ServiceAccount	                         The base workload unit
Service                         Pod (via label selectors)                                        Routes traffic to pods
Ingress                         Service                                                          Routes HTTP(S) to services
PersistentVolumeClaim           PersistentVolume (bound dynamically or statically)               Requests storage from PV
PersistentVolume                Volume plugin driver                                             Static volume declaration
VolumeSnapshot                  PVC                                                              Takes a snapshot of a volume
VolumeSnapshotClass             CSI Drives                                                       Defines the driver/behavior for snapshots
ConfigMap                       None (used by workloads)                                         Used by pods/deployments etc.
Secret                          None (used by workloads)                                         Same as ConfigMap, but sensitive data
NetworkPolicy                   PodSelector                                                      Controls traffic flow between pods
Role / ClusterRole              Resource kinds                                                   Grants access to specific resource types
RoleBinding                     Role                                                             Binds to a Role for namespace access
ClusterRoleBinding              ClusterRole                                                      Binds cluster-wide access
HorizontalPodAutoscaler         Deployment, ReplicaSet, StatefulSet                              Targets workloads to scale
ServiceAccount                  Used by Pods                                                     Binds to RBAC
PodDisruptionBudget             Deployment, StatefulSet, RS                                      Limits voluntary disruptions
CustomResourceDefinition (CRD)  Defines custom resource kinds                                    Extends Kubernetes API
LimitRange / ResourceQuota      Namespace scoped; affects Pods, PVCs                             Limits usage in a namespace
