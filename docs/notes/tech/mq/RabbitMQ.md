
### How to guarantee message delivery reliability?
- Publisher confirm, publisher => Broker
- Consumer acknowledge, Queue => Consumer
    - Manual Ack: When Consumers Fail or Lose Connection: Automatic Requeueing
    - Automatic ACk: should be considered unsafe, consumers's TCP connection or channel is closed before successful delivery, the message sent by the server will be lost.
    - Acknowledgement mode and QoS prefetch value have significant effect on consumer throughput. 
- Clustering
- Resource Monitor & Alarms & Health Checks

### How to identified deliveries?
- Delivery tags
    - Delivery tags are monotonically growing positive integers
    - delivery tags are scoped per channel
    - deliveries must be acknowledged on the same channel they were received on

### What is Quorum Queues/Replicated Queues/?
- https://www.rabbitmq.com/quorum-queues.html
- https://www.rabbitmq.com/streams.html


### How to implement Exchange to exchange bindings in RabbitMQ?
- Exchange-to-exchange bindings improve decoupling, increase topology flexibility, reduce binding churn, and help increase performance
- https://www.cloudamqp.com/blog/exchange-to-exchange-binding-in-rabbitmq.html
- http://skillachie.com/2014/06/27/rabbitmq-exchange-to-exchange-bindings-ampq/

### How to implement Dead letter queue/Delay task?
- https://zoltanaltfatter.com/2016/09/06/dead-letter-queue-configuration-rabbitmq/

### How to achieve RPC?


### AMQP 0-9-1 Module

![](https://www.rabbitmq.com/img/tutorials/intro/hello-world-example-routing.png)

!!!Abstract

    === "Message"
        - ==Messages are load balanced between consumers and not between queues.==
        - Message Acknowledgements		
            - the automatic acknowledgement model(After broker sends a message to an application)
            - the explicit acknowledgement model(After the application sends back an acknowledgement)
        - Message Payload
        
    === "Exchange"
        - Exchanges(Type: Direct/Topic/Headers/Fanout/Default)
            - The default exchange is a direct exchange with no name (empty string) 
            - ==Headers and Fanout Exchanges ignore the routing key attribute==
            - Topic Exchanges route messages to one or many queues based on matching between a message Routing key and the Pattern that was used to bind a queue to an exchange.
		    - The topic exchange type is often used to implement various publish/subscribe pattern variations. 
	    - Binds	
            - Bindings are rules that exchanges use (among other things) to route messages to queues. 
		    - The purpose of the routing key is to select certain messages published to an exchange to be routed to the bound queue. In other words, the routing key acts like a filter.
	
    === "Queue"
		- Durable queues are persisted to disk and thus survive broker restarts. 
		- Queues that are not durable are called transient. 
    
    === "Consumers"
        - Have messages delivered to them ("push API")/Fetch messages as needed ("pull API")
        - Each consumer (subscription) has an identifier called a consumer tag. 
    

	=== "Connections"	
		- AMQP connections are typically long-lived.
		- AMQP is an application level protocol that uses TCP for reliable delivery. 
    
    === "Channels" 
        - AMQP 0-9-1 connections are multiplexed with channels that can be thought of as "lightweight connections that share a single TCP connection".
    
    === "Virtual Hosts" 
        - Multiple isolated "environments" 
  
  
 
### Refer
 - [AMQP 0-9-1 Model Explained](https://www.rabbitmq.com/tutorials/amqp-concepts.html) 
 - [Understanding AMQP, the protocol used by RabbitMQ](https://spring.io/blog/2010/06/14/understanding-amqp-the-protocol-used-by-rabbitmq/) 
    - for learn to write
 - [RabbitMQ for beginners - What is RabbitMQ?](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html) 
 - [Routing Topologies for Performance and Scalability with RabbitMQ](https://spring.io/blog/2011/04/01/routing-topologies-for-performance-and-scalability-with-rabbitmq/) 
  