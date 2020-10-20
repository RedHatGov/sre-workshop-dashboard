# Autoscaling 

## Solution

Please make sure to attempt the lab on your own before viewing the solution!

<details>
  <summary>Click here for the solution</summary>

  Take a look at the events:

  ```execute
  oc get events
  ```

  You should see an event that says:

  ```
  Scaled replication controller "app-ui-1" from 1 to 0
  ```

  The HPA does not act on this either to scale it back up.

  ```execute
  oc describe hpa app-ui
  ```

  One of the conditions will say:

  ```
  ScalingActive  False   ScalingDisabled    scaling is disabled since the replica count of the target is zero  
  ```

  So the core issue is that the replica count for `app-ui` was set to zero.  How did this happen?

  If you look at the spec you deployed:

  ```execute
  cat sre-workshop-code/scenarios/autoscaling/app-ui-autoscale.yaml
  ```

  The `replicas` field is empty.  If you don't include a value for `replicas`, OpenShift will set this value to zero by default.  Hence, the solution is to deploy a `HPA` without modifying the `DeploymentConfig`.

  In a real world setting, you might imagine making this mistake if you **initially** deploy a DeploymentConfig and HPA at the same time.  You might leave the replicas field out, assuming that the HPA will set this correctly on initial deployment.
  
  For the bonus question, it turns out a `Deployment` without `spec.replicas` changes the replica count to 1, so the HPA can still scale the application.  However, dropping the replica count to 1 can negatively impact your application if your replicas were serving live traffic.
  
</details>

## Summary

If you are interested, the inspiration for this scenario is [here][1].

[1]: https://github.com/kubernetes/kubernetes/issues/67135