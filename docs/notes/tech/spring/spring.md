
### Q/A

- how many ways to definite bean?
    - XML file
    - Properties file
    - Annotation config
    
- how to declare Bean?
    - different between `@Component vs @Bean`?
        - [Spring: @Component versus @Bean](https://stackoverflow.com/questions/10604298/spring-component-versus-bean)
    - different between Java based Configuration vs Annotation based Configuration？
        - [Java-based vs annotation-based configuration/autowiring](https://stackoverflow.com/questions/41615041/java-based-vs-annotation-based-configuration-autowiring)

- different between `BeanFactoryPostProcessor` and `BeanFactoryPostProcessor`?
    - [ref](https://www.cnblogs.com/duanxz/p/3750725.html)
    
- how many strategies for creating bean instances?

- Spring Container loading process ?
    - creating bean factory(default `DefaultListableBeanFactory`) 
        - setting InstantiationStrategy
        - reading and loading/register bean definition 
    - configure factory context
        - ClassLoader
        - PropertyEditorRegistrar
        - Spring expression resolver
        - ignore dependency interface
        - register resolvable type
        - Register early post-processor `BeanPostProcessor`
        - detect LoadTimeWeaver and prepare for weaving
        - register default environment bean
    - Spring 容器自带的 `postProcessBeanFactory(beanFactory)` method
        - All bean definitions will have been loaded, but no beans will have been instantiated yet
    - register bean that implement `BeanFactoryPostProcessor` interface
        - `postProcessBeanFactory(ConfigurableListableBeanFactory beanFactory);`
        - Factory hook that allows for custom modification of an application context's bean definitions, adapting the bean property values of the context's underlying bean factory.
        - All bean definitions will have been loaded, but no beans will have been instantiated yet
        - Invoke `BeanDefinitionRegistryPostProcessors` first (implement PriorityOrdered => implement Ordered => regular)
        - `BeanFactoryPostProcessor` that implement PriorityOrdered => implement `Ordered` => regular implement `BeanFactoryPostProcessor` only
    - register bean that implement `BeanPostProcessor` interface
        - Factory hook that allows for custom modification of new bean instances 
        - Apply `postProcessBeforeInitialization` method to the given new bean instance before any bean initialization callbacks
        - Apply `postProcessAfterInitialization` to the given new bean instance after any bean initialization callback
        - register `BeanPostProcessors` that implement `PriorityOrdered` => implement `Ordered` => regular implement `BeanPostProcessor` only
    - Instantiate all non-lazy-init singletons.
        - `finishBeanFactoryInitialization(beanFactory)` => `beanFactory.preInstantiateSingletons()` 
    
- what is Java Flight Recorder?

- `BeanFactoryPostProcessor` used for bootstrapping processing ?
    - `ConfigurationClassPostProcessor`
        - Registered by default when using `<context:annotation-config/>` or `<context:component-scan/>`.
        - This post processor is priority-ordered as it is important that any `@Bean` methods declared in `@Configuration` classes have their corresponding bean definitions registered before any other `BeanFactoryPostProcessor` executes.

- `BeanPostProcessor` used for bootstrapping processing or mainly for internal use ?
    - `MergedBeanDefinitionPostProcessor`
    - `InstantiationAwareBeanPostProcessor`
        - `SmartInstantiationAwareBeanPostProcessor`


### Reference
- [Spring](https://muyinchen.github.io/tags/Spring/)
- [tiny-spring](https://www.zybuluo.com/dugu9sword/note/38274)
- [Spring-1](https://www.cnblogs.com/binarylei/p/10198698.html)
- [spring核心编程思想目录](https://www.cnblogs.com/binarylei/category/1644588.html)
- [Spring IOC核心源码学习](https://web.archive.org/web/20190617021451/http://yikun.github.io/2015/05/29/Spring-IOC%E6%A0%B8%E5%BF%83%E6%BA%90%E7%A0%81%E5%AD%A6%E4%B9%A0)
- [History of Spring Framework and Spring Boot](https://www.quickprogrammingtips.com/spring-boot/history-of-spring-framework-and-spring-boot.html)