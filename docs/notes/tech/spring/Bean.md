# createBean(): 
- Central method of this class: creates a bean instance, populates the bean instance, applies post-processors, etc.

## resolveBeanClass(): Resolve the bean class for the specified bean definition

## resolveBeforeInstantiation(): Apply before-instantiation post-processors
- => applyBeanPostProcessorsBeforeInstantiation()
- => applyBeanPostProcessorsAfterInitialization()
        
## **doCreateBean(): Actually create the specified bean**

### createBeanInstance(): 
- resolveBeanClass()
    => to check modifier is public & whether to allow access to non-public constructors and methods 
    => using instantiation strategy to instantiate bean: factory method/constructor autowiring/simple instantiation 
- InstanceSupplier判断，Specify a callback for creating an instance of the bean
    - Y -> obtainFromSupplier()
- instantiateUsingFactoryMethod判断
    - Y -> instantiateUsingFactoryMethod()
- autowireConstructor：
    - Y -> autowireConstructor():"autowire constructor" (with constructor arguments by type) behavior.
- ==instantiateBean()==: Instantiate the given bean using its default constructor.
    - InstantiationStrategy instantiate

⇓

applying post-processor `MergedBeanDefinitionPostProcessor`

⇓

### populateBean():

- populate the bean instance with the property value
- => applying `InstantiationAwareBeanPostProcessor` 
- => check autowireModel(By_name or By_type) 
- => applying InstantiationAwareBeanPostProcessor check 
- => applyPropertyValues check 

⇓

### initializeBean(): 

- invokeAwareMethod: BeanNameAware/BeanClassLoaderAware/BeanFactoryAware 
- => **applyBeanPostProcessorsBeforeInitialization** 
- => invokeInitMethods: implement InitializingBean 
    - => customInitMethod
- => **applyBeanPostProcessorsAfterInitialization** 

⇓

**registerDisposableBeanIfNecessary()**

⇓

