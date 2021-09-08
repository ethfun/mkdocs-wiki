
!!! Technology Mapping
    
    === "Microservices Concerns"
        ![Microservices Concerns](https://developers.redhat.com/sites/default/files/styles/article_floated/public/blog/2016/12/screen-shot-2016-12-06-at-10-37-37.png?itok=N1fDqQ_y)

    === "Microservices Requirements"
        ![Microservices Requirements](https://developers.redhat.com/sites/default/files/styles/article_floated/public/blog/2016/12/screen-shot-2016-12-06-at-10-30-08.png?itok=av35fUTQ)
    
    === "Microservices Stack"
        ![Microservices Stack](https://developers.redhat.com/sites/default/files/styles/article_floated/public/blog/2016/12/stack-page-1.png?itok=xb7TvIHv)
        
    === "Infrastructure"
        - Git
        - Maven
        - Jenkins
        - Docker
        - Kubernetes
    
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
        - Event sourcing
   
### Tech Stack List
    - API GateWay: Spring Gateway/Zuul
    - Service Discovery/LB: Eureka/Zookeeper
    - Service Deployment/Scale: Git/Jenkins/Docker/Kubernetes
    - Configuration management: Apollo/Spring Cloud config/Nacos
    - Distributed Trace: Spring Sleuth/Zipkin
    - Log: ELK Stash(Elasticsearch/Logstash/kibana) 
    - Resilience & Fault Tolerance: Sentinal/Ribbon
    - Service Security: Spring Security

    
!!! fqa 

    === "Why to choose Microservices?"
        - Pros
            - to facilitate agile application development and deployment
            - technoloy diversity
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
- [Spring Cloud for Microservices Compared to Kubernetes](https://developers.redhat.com/blog/2016/12/09/spring-cloud-for-microservices-compared-to-kubernetes)
- [Event sourcing](https://github.com/cer/event-sourcing-examples/wiki/WhyEventDrivenArch)
