# Introduction to Site Reliability Engineering

<br>

## What is SRE?

Traditional IT Operations teams are built around minimizing and mitigating risk whenever possible. Their monitoring systems are often focused on measuring infrastructure metrics that often describe symptoms of potential problems, but aren't as concerned with the quality of service that the system is providing. 

So what is Site Reliability Engineering (SRE) and what does it aim to solve? SRE builds on the the foundational principles of the DevOps movement by providing a framework to build and maintain reliable services, while encouraging continuous innovation and system improvement. Instead of trying to minimize or eliminate risk, SRE's embrace risk and work to manage the amount of risk in the systems by balancing the stability of the system and the velocity of development of new features being introduced.

This accomplished by deploying their software in on highly automated, deterministic platforms, and recording as much data about the system as possible by leveraging monitoring and log aggregation systems. Having that data, they are able to build a picture of the qualitative behaviors of the system and how that relates to the goals of the business. That picture enables SRE's and product owners to set objectives for the performance of the system which allows them to continuously adjust the amount of work that is needed to improve stability versus adding new functionality.

The SRE concepts that we will be discussing were created at Google and they've written several books on the topic to help other organizations, but it's important to remember that your organization will likely have different challenges that you are trying to solve than Google. These are great starting points, but they should evolved to meet the needs of your organization. For simplicity within this workshop, we will be referencing concepts from Google.

In the SRE books, Google outlines the 8 tenets of SRE and goes in depth on each. Since we have limited time for the workshop we will only be touching on the tents that are highlighted:

* Ensuring a Durable Focus on Engineering
* **Pursuing Maximum Change Velocity Without Violating a Service’s SLO**
* **Monitoring**
* Emergency Response
* **Change Management**
* Demand Forecasting and Capacity Planning
* Provisioning
* **Efficiency and Performance**

<br>

## Why SRE?

There are many different reasons why IT organizations are beginning to adopt SRE, but it's most often because product owners are not able to quickly adapt and delivery the experience that the consumer of the product is expecting. For a traditional IT Operations team, they may be experiencing one or more of the following that is contributing to the situation:

* One-off automation scripts and significant amount of manual toil
* Product development teams tossing code over the fence for Ops to run
* Lack of management commitment to invest in Ops
* Siloed knowledge
* Applying duct tape and bail wire on key infrastructure because failure was scorned
* Lack of a cohesive vision around product offerings
* Fighting to keep lights on over pushing new features 

For teams that are already embracing the principles of a DevOps culture, SRE can provide additional structure to a cross-functional team to enable the success of business goals.

<br>

## How to Get Started With SRE?

Implementing a SRE program is a transformational process, but the first step in working to implement SRE concepts is to really understand the business purpose of the application, and what the desired behaviors are for the consumers of the applications. This is not something that the SRE team can do by themselves, it's a team effort that requires input from the product owners of the application, the development team, and the SRE team. Once on you have defined your objectives, it is important to ensure that you can collect all the metrics you need to identify the behaviors described in the objective.

We will dive deeper into these concepts in the next lab.

<br>

## Summary

In this lab we discussed what Site Reliability Engineering is, why it's beneficial to implement and how we can get started. Next we're going to discuss some important terminology that SRE team use to describe how their systems are performing, and how to measure how much risk is in the system.