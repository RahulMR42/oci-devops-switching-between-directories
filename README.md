This is a fork with multiple TF exmaple of various CSP .

Add - ons 

-----

- Added build_spec.yaml to use it behind an OCI devops build pipeline.
  -  documentation - https://docs.oracle.com/en-us/iaas/Content/devops/using/home.htm 

  - We do use two build params to call the contents dynamically change the tf root path.

  ![](images/build_params.png)     

  - This will help to switch TF root with parameters while invoking the build pipelines (be it via console ,cli ,api or via terraform).