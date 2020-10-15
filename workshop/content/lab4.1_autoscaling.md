# Autoscaling

## Background

At this point in the workshop, we present to you a number of scenarios to enact with your microservices application.  Each scenario causes some type of change that impacts your SLO.  As the SRE, it is your mission to ensure the uptime of the application as you enact these scenarios.

Note: None of these scenarios require you to make changes to the application code!

In this scenario, you are going to add [autoscaling][1] to the application using the Horizontal Pod Autoscaler.  This is a fundamental capability in OpenShift.  Everything looks healthy right now, so let's go ahead and make this change.

## Run

Make sure you are sending traffic to the app if you aren't already:

```execute
while true; do curl -s -o /dev/null $GATEWAY_URL; done
```

Add autoscaling:

```execute
oc apply -f scenarios/autoscaling/app-ui-autoscale.yaml
```

Open your dashboard.  Wait a minute and hit the refresh icon in the top right:

<img src="images/grafana-alert-test-refresh.png" width="600"><br/>

<br>

Your SLOs are breached, and the error budgets are depleted:

<img src="images/grafana-alert-test-unhealthy.png" width="600"><br/>

<br>

Open the application in the browser:

```execute
echo $GATEWAY_URL
```

It returns `no healthy upstream`.  Not good.  Your application is inaccessible, and your users are very unhappy.

## Triage

What went wrong?  This is an exercise for you to find out as the SRE!

Identify:
* How to roll back this change to a previous healthy state
* What factors contributed to the failure?
* How to fix the issue and add autoscaling successfully

Bonus:
* Would this behavior change with a `Deployment` instead of `DeploymentConfig`?  How?

<details>
  <summary>Click here if you need help!</summary>



</details>

## End

Leave autoscaling on once you complete this scenario.

**DO NOT PROCEED** to the next lab until you are ready to view the solution!

[1]: https://docs.openshift.com/container-platform/4.5/nodes/pods/nodes-pods-autoscaling.html