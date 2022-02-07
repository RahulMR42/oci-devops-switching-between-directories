This is a fork with multiple TF exmaple of various CSP .

Add - ons 

-----

- Added build_spec.yaml to use it behind an OCI devops build pipeline.
  -  documentation - https://docs.oracle.com/en-us/iaas/Content/devops/using/home.htm 

  - We do use two build params to call the contents dynamically change the tf root path.

  ![](images/build_params.png)     

  - This will help to switch TF root based on  parameters while invoking the build pipelines (be it via console ,cli ,api sdks or via terraform).


- An example of build run with OCI CLI as follows 

```
oci devops build-run create --build-pipeline-id ocid1.devopsbuildpipeline.oc1.iad.xxxx --build-run-arguments '{ "items": [ { "name": "TF_RESOURC_REFERENCE", "value": "create-vcn" }, { "name": "TF_PROVIDER_PATH", "value": "terraform-provider-oci" } ] }'

```


- OCI CLI documentation - https://docs.oracle.com/en-us/iaas/Content/devops/using/run_build.htm#runbuild_cli  
- Details view of OCI CLI with build run - https://docs.oracle.com/en-us/iaas/tools/oci-cli/3.4.4/oci_cli_docs/cmdref/devops/build-run.html 


Sample exeuction via OCI CLI and snippets from corresponding build run.

----

#### Use OCI TF Provider and resource type as OCU launch-instance 


```
$ oci devops build-run create --build-pipeline-id ocid1.devopsbuildpipeline.oc1.iad.xxjq --build-run-arguments '{ "items": [ { "name": "TF_RESOURC_REFERENCE", "value": "launch-instance" }, { "name": "TF_PROVIDER_PATH", "value": "terraform-provider-oci" } ] }'  

```

![](images/oci_launch_instance.png)


#### Use OCI TF Provider and resource type as OCI create-vcn

```
$ oci devops build-run create --build-pipeline-id ocid1.devopsbuildpipeline.oc1.iad.xxjq  --build-run-arguments '{ "items": [ { "name": "TF_RESOURC_REFERENCE", "value": "create-vcn" }, { "name": "TF_PROVIDER_PATH", "value": "terraform-provider-oci" } ] }' – Same pipeline ,with OCI buit this time with create-vcn resource 
```

![](images/oci_vcn.png)


#### Use GCP  TF Provider and resource type as GCP create-vpc

```
$ oci devops build-run create --build-pipeline-id ocid1.devopsbuildpipeline.oc1.iad.xxjq --build-run-arguments '{ "items": [ { "name": "TF_RESOURC_REFERENCE", "value": "create-vpc" }, { "name": "TF_PROVIDER_PATH", "value": "terraform-provider-gcp" } ] }' – In this case switching in to GCP TF with a resource type of GCP 
```

![](images/gcp_vpc.png)