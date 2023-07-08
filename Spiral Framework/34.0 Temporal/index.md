# Temporal

Temporal is an open-source workflow engine that manages and executes reliable, durable, and fault-tolerant workflows in a distributed manner. The only way to use it in PHP is with RoadRunner, which makes it super easy to integrate your PHP app with Temporal.

Temporal allows you to write your workflows and activities in any supported language. For example, you could have a workflow written in PHP, but handle some of the activities with code written in Go or vice versa. This can be really helpful if you have a team with different language preferences, or if you want to take advantage of the strengths of different languages for different tasks.

Temporal is particularly useful in the following scenarios:

1. **Long-running business processes**: Temporal is excellent for managing processes that can take a long time to complete, where you need to maintain state in a reliable way. This could include processes like order fulfillment, payment processing, or user onboarding.

2. **Reliable task scheduling and execution**: Temporal can ensure that tasks are executed reliably, even in the face of server outages or software crashes. This makes it great for any scenario where you need to ensure a task is completed, regardless of what happens to the system.

3. **Complex coordination of tasks**: Temporal provides a framework for orchestrating complex sequences of tasks, including parallel execution, complex decision-making, and error handling. This is useful in scenarios like data processing, where you might need to coordinate a series of different tasks in a particular order.

4. **Distributed transactions**: If you need to perform a series of tasks across different services as part of a single transaction, Temporal can help. It can ensure that all tasks are completed successfully or that compensating transactions are executed if something goes wrong.

5. **Testing and debugging**: Temporal includes testing and debugging tools that make it easier to work with long-running workflows. You can replay workflows, inspect the state of a workflow at any point in time, and even write unit tests for your workflows.

### Links and materials to read more:
1. [Temporal in Spiral Framework](https://spiral.dev/docs/temporal-configuration/current/en)
