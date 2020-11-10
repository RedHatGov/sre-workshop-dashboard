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

In your next status update, you inform your team that you successfully enabled health check probes for better fault tolerance.  Now, OpenShift will restart the application pod if the application falls into an unhealthy state.

Health checks are fundamental capabilities in OpenShift, and it's important to configure health checks probes correctly.  Otherwise, your applications can serve traffic when they are not ready or be unnecessarily restarted.  As a reminder, you can learn more about health check probes in the [OpenShift documentation][1].

[1]: https://docs.openshift.com/container-platform/4.5/applications/application-health.html