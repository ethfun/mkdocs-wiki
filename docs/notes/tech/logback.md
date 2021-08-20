# LogBack logging framework

!!!Design
        
    === "Logback"
        - one of the foremost design goals of logback was speed of execution, a requirement which is second only to reliability.
        - one of the design goals of logback is to audit and debug complex distributed applications
!!!Note        

    === "initialization"
        <pre><div class="mermaid">
        graph LR
            A(to find logback-test.xml) 
            B(to find logback.groovy)
            C(to find SPI implement)
            D(to find logback.xml)
            E(using the default config - BasicConfigurator)
            A -->|N| B -->|N| C -->|N| D -->|N| E;
        </div></pre>

!!!Structure

    === "config structure"
        <pre><div class="mermaid">
        graph LR
            A(configuration) 
            B(appender)
            C(logger)
            D(root)
            A --> B
            A --> C 
            A --> D
        </div></pre>
        
!!! Component

    === "Appender"
        <pre><div class="mermaid">
        graph LR
            Z(Append)
            A(AppenderBase)
            B(OutputStreamAppender)
            C(ConsoleAppender)
            D(FileAppender)
            E(RollingFileAppender)
            F(SiftingAppender)
            G(AsyncAppender)
            H(DBAppender)
            I(SMTPAppender)
            J(SyslogAppender)
            M(DIYAppender)
            N(AsyncAppenderBase)
            O(DBAppenderBase)
            Z --> A;Z --> B;Z --> N;Z --> O
            B --> C;B --> D;B --> E
            A --> F;A --> I;A --> J;A --> M
            N --> G;O --> H
        </div></pre>
    
    === "Layouts"
        - responsible for transforming an incoming event into a String. 
    
    === "Filters"
        - Filters
            - Regular filters
            - Turbor filter
    === "MDC"
        - MDC is the abbreviation of Mapped Diagnostic Context
            - the MDC manages contextual information on a per thread basis
            - to uniquely stamp each request
        - Demo, make sure that MDCInsertingServletFilter is declared before other filters.
        ```Java
            MDCInsertingServletFilter
        ```
    
!!!Summary
    
    === "under the hood"
        <pre><div class="mermaid">
        graph TD
            A[Get the basic selecion rule] --> B[Apply the basic selection rule]
            --> C[Create a LogginEvent Objet] --> D[Invoking appenders]
            --> E[Formatting the output] --> F[Sending out the LoggingEvent]
        </div></pre>

!!!Question
    
    - logback是否支持dynamic修改, auto reload configuration file？
    - springboot admin如何实现动态修改log level?
    - 如何实现动态写日志？
    - What is MDC? 


    