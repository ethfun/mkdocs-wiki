
### Infrastructure
- Git
- Maven
- Jenkins
- Docker
- Kubernetes


### Components
!!! Abstract
    
    === "API Gateway, API-First Design"
        - Facade pattern
        - single entry point into the system
        - routing request

    === "Inter-Process Communication/IPC mechanism"
        - interaction style
            - Request/Response
            - Publish/subscribe
            - Notification (one-way request)
        - "IPC Technology"
            - Message-based communication
            - REST
            - RPC: Dubbo/gRPC/Thrift
        
    === "Service Discovery"
        - client-side discovery pattern & server-side discovery pattern
        - Service Registry
            - Eureka
            - etcd
            - consul
            - zookeeper
        
    === "Event-Driven Data Management"
        - ACID transaction
        - BASE - basically available, soft state, eventually consistent
        - [Event sourcing](https://github.com/cer/event-sourcing-examples/wiki/WhyEventDrivenArch)
        
    
!!! fqa 

    === "Why to choose Microservices?"
        - Pros
            - to facilitate agile application development and deployment
            - to tackles the problem of complexity
            - developed independently
            - deployed independently
            - scaled independently
            
        - Cons
            - complexity arise from Test/Deployment/Business transaction(span service)
     
    === "How to Deploy services?"
        - Multiple Service Instances per Host Pattern
        - Service Instance per Host Pattern
        - Service Instance per Container Pattern
        - Serverless Deployment
        
    === "How to refactor a Monolith into Microservices?"
        - Stop Monolith develop
        - Split Frontend and Backend
        - Extract Service Strategy, prioritizing which module?
            - to start with modules that are easy to extract
            - to rank modules by the benefit you will receive
            
---
- [Introduction to Microservices](https://www.nginx.com/blog/introduction-to-microservices/)