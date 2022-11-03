# HowTo use OpenFlow queues

## Abstract

OpenFlow - is a midddleware and web GUI that, among other things, provide an interface to the RabbitMQ queue system under the hood.

In case if queue processing is required (e.g. to do a web scraping without getting blocked) an OpenFlow feature 'work item queues' shall be used.

On a high level, the idea is that you create and configure the queue on OpenFlow and then you use it through the Node-Red special nodes, that push things to be processed to the queue and pick them up from the queue, with respect to the queue settings.

## How To

1. Go to your OpenFlow - the URL is provided for the cloud version of the OpenFlow: https://app.openiap.io/#/WorkitemQueues

2. Create your Node-Red workflow:
	1. Create new flow
	2. Drag & drop flows.json to the screen
	3. Verify your 'Add Workitem' node has config 'ExampleQueue' -> that's a name of the queue at OpenFlow side -> WorkItem2.png shall be here
	4. On 'ampq consumer' make sure the queue name is 'ExampleConsumer' -> that's a name of the RabbitMQ queue under the hood -> WorkItems3.png shall be here
	5. Click 'Deploy'
	6. Go the queue creation at OpenFlow
   
3. Create your queue:
   ![[WorkItemsQueues1 1.png]]

	1. Fill in 'Name' - ideally with a name without spaces, you will need it later at the Node-Red node configuration
	2. Choose project, workflow & robot (fetches from the one created at OpenRPA)
	3. choose 'amqpqueue' (comes from Node-Red nodes configuration)

4. Go back to Node-Red and verify that all of the nodes configuration is in order
5. Start your flow and go immediately to https://app.openiap.io/#/Workitems - you shall find 'Find me' item with status 'Processing' which shall change to 'successful' after a few seconds, which means, that the item has been pushed to the queue by the first flow, then picked up by a second flow and a status has been changed to 'successful'.
6. Feel free to modify the logic as you see fit!

More information could be found at https://github.com/open-rpa/openrpa/wiki/Workitems