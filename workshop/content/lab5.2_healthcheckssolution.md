# Health Checks

## Solution

Please make sure to attempt the lab on your own before viewing the solution!

<details>
  <summary>Click here for the solution</summary>

  Look at your application pods:

  ```execute
  oc get pods -l app=app-ui
  ```

  The newest version (prefixed by `app-ui-2`) will transition from `CrashLoopBackoff` and will eventually `Error`.

  If you look at the events of that pod:

  ```execute
  oc describe pod -l deployment=app-ui-2
  ```

  You will see the `readinessProbes` and `livenessProbes` repeatedly fail.

  If you look at the probes spec:

  ```execute
  cat scenarios/healthchecks/probes.yaml
  ```

  Notice the only thing that has been defined is the endpoint and port.  If you look at the [documentation][1], there is a field called `timeoutSeconds` that defaults to 1.

  Try hitting the probe endpoint in the application:

  ```execute
  curl $GATEWAY_URL/info
  ```

  It takes longer than 1 second to return.  The solution is to increase the `timeoutSeconds` value so the probes do not fail.
  
</details>

## Summary

[1]: https://docs.openshift.com/container-platform/4.5/applications/application-health.html