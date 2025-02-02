# GKE POC Toolkit - Command Line Interface 

This subdirectory contains code and sample config for the GKE POC Toolkit CLI. This Golang command-line tool wraps the Terraform scripts used to set up a GKE environment consisting of one or more clusters. 


## Configuration 

| Name                        | Type              | Valid Values                                                                               | Default Value                                          |
| --------------------------- | ----------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| `region`                    | string            | any Google Cloud region                                                                    | `us-central1`                                          |
| `terraformState`            | string            | `local,cloud`                                                                              | `local`                                                |
| `configSync`                | bool              | `true,false`                                                                               | `true`                                                |
| `policyController`                | bool              | `true,false`                                                                               | `true`                                                |
| `clustersProjectId`         | string            | `projectId`                                                                                | (you are prompted for your GCP Project ID by the tool) |
| `governanceProjectId`       | string            | `projectId`                                                                                | (you are prompted for your GCP Project ID by the tool) |
| `privateEndpoint`           | string            | `true,false`                                                                               | `false`                                                |
| `enableWorkloadIdentity`    | bool              | `true,false`                                                                               | `true`                                                 |
| `enableWindowsNodepool`     | bool              | `true,false`                                                                               | `false`                                                |
| `enablePreemptibleNodepool` | bool              | `true,false`                                                                               | `false`                                                |
| `defaultNodepoolOS`         | string            | https://cloud.google.com/kubernetes-engine/docs/concepts/node-images#available_node_images | `cos`                                                  |
| `vpcConfig`                 | VpcConfig         | `VpcConfig` values below!                                                                  |                                                        |
| `clustersConfig`            | `[]ClusterConfig` | `ClusterConfig` values below!                                                              |                                                        |

### VpcConfig


| Name                | Type   | Valid Values                                                                        | Default Value                                          |
| ------------------- | ------ | ----------------------------------------------------------------------------------- | ------------------------------------------------------ |
| `vpcConfig.vpcName` | string | any non-empty string                                                                | `"default"`                                            |
| `vpcConfig.vpcType` | string | `shared,standalone`                                                                 | `standalone`                                           |
| `vpcProjectId`      | string | `projectId`                                                                         | (you are prompted for your GCP Project ID by the tool) |  | `podCIDRName` | string |  |  |
| `svcCIDRName`       | string | any non-empty string                                                                | `default`                                              |
| `podCIDRName`       | string | any non-empty string                                                                | `default`                                              |
| `authCIDR`            | string | `cidr notation of IP to allow access to the GKE control plane, example: 1.2.3.4/32` | `0.0.0.0/0`                                |
|                     |

### ClusterConfig


| Name          | Type   | Valid Values                                        | Default Value                                         |
| ------------- | ------ | --------------------------------------------------- | ----------------------------------------------------- |
| `projectId`   | string |                                                     | (you are prompted for your GCP Project ID on startup) |
| `nodeSize`    | int    | 1-100                                               | 3                                                     |
| `machineType` | string | https://cloud.google.com/compute/docs/machine-types | `e2-standard-4`                                       |
| `clusterType` | string | `private,public`                                    | `public`                                              |
| `region`      | string | https://cloud.google.com/compute/docs/regions-zones | `us-central1`                                         |
| `zone`        | string | https://cloud.google.com/compute/docs/regions-zones | `us-central1-b`                                       |
| `subnetName`  | string | any non-empty string                                | `"default"`                                           |
|               |
