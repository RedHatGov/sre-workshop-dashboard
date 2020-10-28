# Cron Job

## Solution

Please make sure to attempt the lab on your own before viewing the solution!

<details>
  <summary>Click here for the solution</summary>

  Look at the cron job you added:

  ```execute
  oc describe cronjob high-cpu-workload
  ```  

  The `concurrencyPolicy` was set to `Allow` even though we actually wanted `Forbid`.  If you compare against the documentation examples, you will see that `concurrencyPolicy`, `successfulJobsHistoryLimit`, and  `failedJobsHistoryLimit` are in the wrong place.  They should be part of the top-level spec, not the template spec describing the container.
  
  This is tricky, since the field was in the wrong place but it was silently ignored, causing the error.

  Additionally, you should add `activeDeadlineSeconds` to protect jobs from running indefinitely. In this case, the simulated workload runs indefinitely, hogging cpu resources.
  
  Here is an example of a correctly configured [Cron Job][2].

</details>

## Summary

If you are interested, the inspiration for this scenario is [here][3].

[1]: https://docs.openshift.com/container-platform/4.5/applications/application-health.html
[2]: https://github.com/theckang/openshift-sre/blob/solutions/solutions/cronjob/cronjob.yaml
[3]: https://youtu.be/LpFApeaGv7A?t=495
