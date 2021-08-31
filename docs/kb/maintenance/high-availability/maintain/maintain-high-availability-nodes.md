---
title: Maintain High Availability nodes
description: Managing the nodes in your Octopus High Availability cluster can be done in the Octopus Web Portal.
position: 30
---

Maintaining the nodes in your Octopus Server High Availability cluster can be done on the **Nodes** tab in the **Configuration** area:


Information regarding each of your nodes is displayed here.  You can see:

- **Name**: the name of the node.
- **Status**: the status of the node (e.g. Running, Drained, Offline).
- **Last seen**: the last time the node checked in.
- **Task cap**: the maximum number of tasks that may run on the node.
- **Tasks**: the number of task currently running on the node.
- **Drain**: on or off depending on if the node can execute new tasks.

## Last seen

Octopus Server nodes will check-in at regular intervals.  If an Octopus Server node goes offline a warning will be displayed and the time that it went offline can be determined by looking at the **last seen** field.


## Tasks

Each Octopus Server node will execute tasks as they are queued. The **tasks** field displays the number of tasks currently running on that node. Following the active tasks link will display more information about all of the tasks for that node.

## Task cap

Each Octopus Server node can execute a maximum number of tasks in parallel.  This is to prevent death by multi-tasking. The **task cap** allows you to configure the maximum number of tasks for each node.  If more tasks are created than the total available task cap, the tasks will queue for up to a day until an Octopus Server node is available to execute the task.

You may consider setting a low cap for your Octopus Servers on poorer hardware or have a dedicated UI node with a low task cap to improve UI performance.

## Drain

The drain toggle can be used to prevent an Octopus Server node from executing any new tasks. While draining:

- An Octopus Server node will finish running any tasks is it currently executing and then idle.
- The Octopus Server ping url will not return 200 OK.

## Load balancing

To distribute HTTP load among Octopus Server nodes with a single point of access it is recommend to use an HTTP load balancer. We typically recommend using a round-robin (or similar) approach for sharing traffic between the nodes in your cluster.

Octopus Server provides a health check endpoint for your load balancer to ping: `/api/octopusservernodes/ping`


Making a standard `HTTP GET` request to this URL on your Octopus Server nodes will return:

- HTTP Status Code `200 OK` as long as the Octopus Server node is online and not in [drain mode](#drain).
- HTTP Status Code `418 I'm a teapot` when the Octopus Server node is online, but it is currently in [drain mode](#drain) preparing for maintenance.
- Anything else indicates the Octopus Server node is offline, or something has gone wrong with this node.

:::hint
The Octopus Server node configuration is also returned as JSON in the HTTP response body.
:::

## Example procedure: Installing Windows updates

One of the great benefits of High Availability is the ability to perform maintenance on one node, while allowing other nodes to continue to perform deployments or server users.

For example, imagine it is time to install Windows Updates on one node. The process would be:

1. Use the *Drain* feature on the **Nodes** page to tell the node to continue executing any deployments that it is currently running, but not to start any new deployments (other nodes in the cluster will take over).
2. Once the node isn't executing any more deployments, remove it from the load balancer.
3. Install updates, restart the node, etc. as required.
4. Add the node back to the load balancer.
5. Disable the *Drain* feature, so that the node can now execute deployments again.
