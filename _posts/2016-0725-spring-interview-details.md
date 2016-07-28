---
layout: post
title: Spring、Hibernate、Mybatis面试相关知识点
date: 2016-07-25 11:40
modified: 2016-07-26 11:40				
category: JAVA
tags: ["JAVA","spring"]
excerpt: Spring、Hibernate、Mybatis面试相关知识点
comments: true
---



### Spring 基础知识

1. 什么是spring?
	
	Spring 是个java企业级应用的开源开发框架。Spring主要用来开发Java应用，但是有些扩展是针对构建J2EE平台的web应用。Spring 框架目标是简化Java企业级应用开发，并通过POJO为基础的编程模型促进良好的编程习惯。

2. 使用Spring框架的好处是什么？

	* 轻量：Spring 是轻量的，基本的版本大约2MB。
	* 控制反转：Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们。
	* 面向切面的编程(AOP)：Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开。
	* 容器：Spring 包含并管理应用中对象的生命周期和配置。
	* MVC框架：Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品。
	* 事务管理：Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）。
	* 异常处理：Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。

3.  Spring由哪些模块组成?

	以下是Spring 框架的基本模块：

	* 	Core module
	* 	Bean module
	* 	Context module
	* 	Expression Language module
	* 	JDBC module
	* 	ORM module
	* 	OXM module
	* 	Java Messaging Service(JMS) module
	* 	Transaction module
	* 	Web module
	* 	Web-Servlet module
	* 	Web-Struts module
	* 	Web-Portlet module

4. 核心容器（应用上下文) 模块。

	这是基本的Spring模块，提供Spring框架的基础功能，BeanFactory是任何以spring为基础的应用的核心。Spring框架建立在此模块之上，它使Spring成为一个容器。

5. BeanFactory – BeanFactory实现举例。

	Bean工厂是工厂模式的一个实现，提供了控制反转功能，用来把应用的配置和依赖从正真的应用代码中分离。

	最常用的BeanFactory 实现是XmlBeanFactory 类。

6. XMLBeanFactory 

	最常用的就是org.springframework.beans.factory.xml.XmlBeanFactory，它根据XML文件中的定义加载beans。该容器从XML文件读取配置元数据并用它去创建一个完全配置的系统或应用。

7. 解释AOP模块

	AOP模块用于发给我们的Spring应用做面向切面的开发， 很多支持由AOP联盟提供，这样就确保了Spring和其他AOP框架的共通性。这个模块将元数据编程引入Spring。

8. 解释JDBC抽象和DAO模块。

	通过使用JDBC抽象和DAO模块，保证数据库代码的简洁，并能避免数据库资源错误关闭导致的问题，它在各种不同的数据库的错误信息之上，提供了一个统一的异常访问层。它还利用Spring的AOP模块给Spring应用中的对象提供事务管理服务。

9. 解释对象/关系映射集成模块。

	Spring通过提供ORM模块，支持我们在直接JDBC之上使用一个对象/关系映射映射(ORM)工具，Spring 支持集成主流的ORM框架，如Hibernate,JDO和iBATIS SQL Maps。Spring的事务管理同样支持以上所有ORM框架及JDBC。

10. 解释WEB模块。

	Spring的WEB模块是构建在application context 模块基础之上，提供一个适合web应用的上下文。这个模块也包括支持多种面向web的任务，如透明地处理多个文件上传请求和程序级请求参数的绑定到你的业务对象。它也有对Jakarta Struts的支持。

12.  Spring配置文件

	Spring配置文件是个XML文件，这个文件包含了类信息，描述了如何配置它们，以及如何相互调用。

13.  什么是Spring IOC容器？

	Spring IOC负责创建对象，管理对象（通过依赖注入（DI），装配对象，配置对象，并且管理这些对象的整个生命周期。

14.  IOC的优点是什么？

	IOC或依赖注入把应用的代码量降到最低。它使应用容易测试，单元测试不再需要单例和JNDI查找机制。最小的代价和最小的侵入性使松散耦合得以实现。IOC容器支持加载服务时的饿汉式初始化和懒加载。

15. ApplicationContext通常的实现是什么?

	* FileSystemXmlApplicationContext：此容器从一个XML文件中加载beans的定义，XML Bean 配置文件的全路径名必须提供给它的构造函数。
	* ClassPathXmlApplicationContext：此容器也从一个XML文件中加载beans的定义，这里，你需要正确设置classpath因为这个容器将在classpath里找bean配置。
	* WebXmlApplicationContext：此容器加载一个XML文件，此文件定义了一个WEB应用的所有bean。

16. Bean工厂和 Application contexts有什么区别？

	Application contexts提供一种方法处理文本消息，一个通常的做法是加载文件资源（比如镜像），它们可以向注册为监听器的bean发布事件。另外，在容器或容器内的对象上执行的那些不得不由bean工厂以程序化方式处理的操作，可以在Application contexts中以声明的方式处理。Application contexts实现了MessageSource接口，该接口的实现以可插拔的方式提供获取本地化消息的方法。

17. 一个Spring的应用看起来象什么？

	* 一个定义了一些功能的接口。
	* 这实现包括属性，它的setter、getter方法和函数等。
	* Spring AOP。
	* Spring 的XML配置文件。
	* 使用以上功能的客户端程序。
	* 依赖注入。

18. **什么是Spring的依赖注入**？

	依赖注入，是IOC的一个方面，是个通常的概念，它有多种解释。这概念是说你不用创建对象，而只需要描述它如何被创建。你不在代码里直接组装你的组件和服务，但是要在配置文件里描述哪些组件需要哪些服务，之后一个容器（IOC容器）负责把他们组装起来。

19.  有哪些不同类型的IOC（依赖注入）方式？

	1. 构造器依赖注入：构造器依赖注入通过容器触发一个类的构造器来实现的，该类有一系列参数，每个参数代表一个对其他类的依赖。
	2. Setter方法注入：setter方法注入是容器通过调用无参构造器或无参static工厂方法实例化bean之后，调用该bean的setter方法，即实现了基于setter的依赖注入。
	
20. 哪种依赖注入方式你建议使用，构造器注入，还是 Setter方法注入？

	* 你两种依赖方式都可以使用，构造器注入和Setter方法注入。
	* `最好的解决方案是用构造器参数实现强制依赖，setter方法实现可选依赖`。

### Spring bean
21. 什么是Spring beans?

	Spring beans是那些形成Spring应用的主干的java对象。它们被Spring IOC容器初始化、装配和管理。这些beans通过容器中配置的元数据创建。比如，以XML文件中\<bean/\> 的形式定义。

	Spring框架定义的beans都是单件beans。在bean tag中有个属性”singleton”，如果它被赋为TRUE，bean就是单件，否则就是一个prototype bean。默认是TRUE，所以所有`在Spring框架中的beans缺省都是单件`。

22. 一个 Spring Bean定义包含什么？

	一个Spring Bean的定义包含容器必知的所有配置元数据，包括如何创建一个bean，它的生命周期详情及它的依赖。

23. 如何给Spring容器提供配置元数据?

	1. XML配置文件。

	2. 基于注解的配置。

	3. 基于java的配置。

24. 你怎样定义类的作用域? 

	XML配置方式如下：
	
	```
	<bean id="userService" class="com.xg.service.UserServiceImpl" scope="singleton"/>
	```

	当定义一个`<bean>` 在Spring里，我们还能给这个bean声明一个作用域。它可以通过bean定义中的scope属性来定义。如当Spring要在需要的时候每次生产一个新的bean实例，bean的scope属性被指定为prototype。另一方面，一个bean每次使用的时候必须返回同一个实例，这个bean的scope属性必须设为singleton。

25. 解释Spring支持的几种bean的作用域。

	request、session和global-session作用域仅在基于web的Spring ApplicationContext情形下有效。
	* singleton : bean在每个Spring IOC 容器中只有一个实例。
	* prototype：一个bean的定义可以有多个实例。根据经验，对有状态的bean应该使用prototype作用域，而对无状态的bean则应该使用singleton作用域。
	* request：`每次http请求`都会创建一个bean。
	* session：在`一个HTTP Session`中，一个bean定义对应一个实例。
	* global-session：在一个`全局的HTTP Session`中，一个bean定义对应一个实例。
	
	缺省的Spring bean的作用域是Singleton.   

26. Spring框架中的单例bean是线程安全的吗?

	不，Spring框架中的单例bean不是线程安全的。
	
	>  　　单例模式的意思就是只有一个实例。单例模式确保某一个类只有一个实例，而且自行实例化并向整个系统提供这个实例。这个类称为单例类。
	
	>  　　当多用户同时请求一个服务时，容器会给每一个请求分配一个线程，这是多个线程会并发执行该请求多对应的业务逻辑（成员方法），此时就要注意了，如果该处理逻辑中有对该单列状态的修改（体现为该单列的成员属性），则必须考虑线程同步问题。
	
	> **同步机制的比较**　  
	　
	>  　　ThreadLocal和线程同步机制相比有什么优势呢？ThreadLocal和线程同步机制都是为了解决多线程中相同变量的访问冲突问题。 
	
	> 　　在同步机制中，通过对象的锁机制保证同一时间只有一个线程访问变量。这时该变量是多个线程共享的，使用同步机制要求程序慎密地分析什么时候对变量进行读写，什么时候需要锁定某个对象，什么时候释放对象锁等繁杂的问题，程序设计和编写难度相对较大。 
	
	> 　　而ThreadLocal则从另一个角度来解决多线程的并发访问。ThreadLocal会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。ThreadLocal提供了线程安全的共享对象，在编写多线程代码时，可以把不安全的变量封装进ThreadLocal。 
	
	> 　　由于ThreadLocal中可以持有任何类型的对象，低版本JDK所提供的get()返回的是Object对象，需要强制类型转换。但JDK 5.0通过泛型很好的解决了这个问题，在一定程度地简化ThreadLocal的使用
	
	> 　　概括起来说，对于多线程资源共享的问题，同步机制采用了“以时间换空间”的方式，而ThreadLocal采用了“以空间换时间”的方式。前者仅提供一份变量，让不同的线程排队访问，而后者为每一个线程都提供了一份变量，因此可以同时访问而互不影响。
	 
	> 	`Spring使用ThreadLocal解决线程安全问题` 
	
	> 　　我们知道在一般情况下，只有无状态的Bean才可以在多线程环境下共享，在Spring中，绝大部分Bean都可以声明为singleton作用域。就是因为Spring对一些Bean（如RequestContextHolder、TransactionSynchronizationManager、LocaleContextHolder等）中非线程安全状态采用ThreadLocal进行处理，让它们也成为线程安全的状态，因为有状态的Bean就可以在多线程中共享了。 
	
	> 　　一般的Web应用划分为展现层、服务层和持久层三个层次，在不同的层中编写对应的逻辑，下层通过接口向上层开放功能调用。在一般情况下，从接收请求到返回响应所经过的所有程序调用都同属于一个线程。
	
	> 　　ThreadLocal是解决线程安全问题一个很好的思路，它通过为每个线程提供一个独立的变量副本解决了变量并发访问的冲突问题。在很多情况下，ThreadLocal比直接使用synchronized同步机制解决线程安全问题更简单，更方便，且结果程序拥有更高的并发性。
	 
	>  　　如果你的代码所在的进程中有多个线程在同时运行，而这些线程可能会同时运行这段代码。如果每次运行结果和单线程运行的结果是一样的，而且其他的变量的值也和预期的是一样的，就是线程安全的。 或者说:一个类或者程序所提供的接口对于线程来说是原子操作或者多个线程之间的切换不会导致该接口的执行结果存在二义性,也就是说我们不用考虑同步的问题。 　线程安全问题都是由全局变量及静态变量引起的。 
	 
	>  　　若每个线程中对全局变量、静态变量只有读操作，而无写操作，一般来说，这个全局变量是线程安全的；若有多个线程同时执行写操作，一般都需要考虑线程同步，否则就可能影响线程安全。
	
	> 1. 常量始终是线程安全的，因为只存在读操作。 
	> 2. 每次调用方法前都新建一个实例是线程安全的，因为不会访问共享的资源。
	> 3. 局部变量是线程安全的。因为每执行一个方法，都会在独立的空间创建局部变量，它不是共享的资源。局部变量包括方法的参数变量和方法内变量。
	> 4. 有状态就是有数据存储功能。有状态对象(Stateful Bean)，就是有实例变量的对象 ，可以保存数据，是非线程安全的。在不同方法调用间不保留任何状态。
	> 5. 无状态就是一次操作，不能保存数据。无状态对象(Stateless Bean)，就是没有实例变量的对象。不能保存数据，是不变类，是线程安全的。
	
	>  　　无状态的Bean适合用不变模式，技术就是单例模式，这样可以共享实例，提高性能。有状态的Bean，多线程环境下不安全，那么适合用Prototype原型模式。Prototype: 每次对bean的请求都会创建一个新的bean实例。
	
	>  　　Struts2默认的实现是Prototype模式。也就是每个请求都新生成一个Action实例，所以不存在线程安全问题。需要注意的是，如果由Spring管理action的生命周期， scope要配成prototype作用域。

27. 解释Spring框架中bean的生命周期。

	1. Spring容器从XML文件中读取bean的定义，并实例化bean。
	2. Spring根据bean的定义填充所有的属性。
	3. 如果bean实现了BeanNameAware接口，Spring传递bean的ID到setBeanName方法。
	4. 如果bean实现了BeanFactoryAware接口，Spring传递beanFactory给setBeanFactory方法。
	5. 如果有任何与bean相关联的BeanPostProcessors，Spring会在postProcesserBeforeInitialization()方法内调用它们。
	6. 如果bean实现IntializingBean了，调用它的afterPropertySet方法，如果bean声明了初始化方法，调用此初始化方法。
	7. 如果有BeanPostProcessors和bean关联，这些bean的postProcessAfterInitialization()方法将被调用。
	8. 如果bean实现了DisposableBean，它将调用destroy()方法。

28.  哪些是重要的bean生命周期方法？你能重载它们吗？

	有两个重要的bean生命周期方法，第一个是setup，它是在容器加载bean的时候被调用。第二个方法是teardown它是在容器卸载类的时候被调用。

	The bean标签有两个重要的属性（init-method和destroy-method）。用它们你可以自己定制初始化和注销方法。它们也有相应的注解（@PostConstruct和@PreDestroy）。

29. 什么是Spring的内部bean？

	当一个bean仅被用作另一个bean的属性时，它能被声明为一个内部bean，为了定义inner bean，在Spring的基于XML的配置元数据中，可以在`<property/>`或`<constructor-arg/>`元素内使用`<bean/>`元素，内部bean通常是匿名的，它们的Scope一般是prototype。

30. 在 Spring中如何注入一个java集合？

	Spring提供以下几种集合的配置元素：

	1. <list>类型用于注入一列值，允许有相同的值。
	2. <set> 类型用于注入一组值，不允许有相同的值。
	3. <map> 类型用于注入一组键值对，键和值都可以为任意类型。
	4. <props> 类型用于注入一组键值对，键和值都只能为String类型。

31. 什么是bean装配? 

	装配，或bean装配是指在Spring容器中把bean组装到一起，前提是容器需要知道bean的依赖关系，如何通过依赖注入来把它们装配到一起。

32. 什么是bean的自动装配？

	Spring容器能够自动装配相互合作的bean，这意味着容器不需要`<constructor-arg>`和`<property>`配置，能通过Bean工厂自动处理bean之间的协作。

33. 解释不同方式的自动装配。

	有五种自动装配的方式，可以用来指导Spring容器用自动装配方式来进行依赖注入。

	* no：默认的方式是不进行自动装配，通过显式设置ref属性来进行装配。
	* byName：通过参数名自动装配，Spring容器在配置文件中发现bean的autowire属性被设置成byname，之后容器试图匹配、装配和该bean的属性具有相同名字的bean。
	* byType:：通过参数类型自动装配，Spring容器在配置文件中发现bean的autowire属性被设置成byType，之后容器试图匹配、装配和该bean的属性具有相同类型的bean。如果有多个bean符合条件，则抛出错误。
	* constructor：这个方式类似于byType，但是要提供给构造器参数，如果没有确定的带参数的构造器参数类型，将会抛出异常。
	* autodetect：首先尝试使用constructor来自动装配，如果无法工作，则使用byType方式。

34. 自动装配有哪些局限性?

	自动装配的局限性是：
	* 重写：你仍需用`<constructor-arg>`和`<property>`配置来定义依赖，意味着总要重写自动装配。
	* 基本数据类型：你不能自动装配简单的属性，如基本数据类型，String字符串，和类。
	* 模糊特性：自动装配不如显式装配精确，如果有可能，建议使用显式装配。

35. 你可以在Spring中注入一个null和一个空字符串吗？

	可以。

### Spring注解

36. 什么是基于Java的Spring注解配置? 给一些注解的例子.

	基于Java的配置，允许你在少量的Java注解的帮助下，进行你的大部分Spring配置而非通过XML文件。

	以@Configuration 注解为例，它用来标记类可以当做一个bean的定义，被Spring IOC容器使用。另一个例子是@Bean注解，它表示此方法将要返回一个对象，作为一个bean注册进Spring应用上下文。

37. 什么是基于注解的容器配置?

	相对于XML文件，注解型的配置依赖于通过字节码元数据装配组件，而非尖括号的声明。

	开发者通过在相应的类，方法或属性上使用注解的方式，直接组件类中进行配置，而不是使用xml表述bean的装配关系。

38. 怎样开启注解装配？

	注解装配在默认情况下是不开启的，为了使用注解装配，我们必须在Spring配置文件中配置 \<context:annotation-config/\>元素。

39. @Required注解

	这个注解表明bean的属性必须在配置的时候设置，通过一个bean定义的显式的属性值或通过自动装配，若@Required注解的bean属性未被设置，容器将抛出BeanInitializationException。

40. @Autowired注解

	@Autowired注解提供了更细粒度的控制，包括在何处以及如何完成自动装配。它的用法和@Required一样，修饰setter方法、构造器、属性或者具有任意名称和/或多个参数的PN方法。

41. @Qualifier注解

	当有多个相同类型的bean却只有一个需要自动装配时，将@Qualifier 注解和@Autowire 注解结合使用以消除这种混淆，指定需要装配的确切的bean。

### Spring数据访问

42. 在Spring框架中如何更有效地使用JDBC? 

	使用SpringJDBC 框架，资源管理和错误处理的代价都会被减轻。所以开发者只需写statements 和 queries从数据存取数据，JDBC也可以在Spring框架提供的模板类的帮助下更有效地被使用，这个模板叫JdbcTemplate （例子见这里here）

43. JdbcTemplate

	JdbcTemplate 类提供了很多便利的方法解决诸如把数据库数据转变成基本数据类型或对象，执行写好的或可调用的数据库操作语句，提供自定义的数据错误处理。

44. Spring对DAO的支持

	Spring对数据访问对象（DAO）的支持旨在简化它和数据访问技术如JDBC，Hibernate or JDO 结合使用。这使我们可以方便切换持久层。编码时也不用担心会捕获每种技术特有的异常。

45. 使用Spring通过什么方式访问Hibernate? 

	在Spring中有两种方式访问Hibernate：

	控制反转  Hibernate Template和 Callback。
	继承 HibernateDAOSupport提供一个AOP 拦截器。

46. Spring支持的ORM

	Spring支持以下ORM：
	
	* 	Hibernate
	* 	iBatis
	* 	JPA (Java Persistence API)
	* 	TopLink
	* 	JDO (Java Data Objects)
	* 	OJB

47. 如何通过HibernateDaoSupport将Spring和Hibernate结合起来？

	用Spring的 SessionFactory 调用 LocalSessionFactory。集成过程分三步：
	1. 配置the Hibernate SessionFactory。
	2. 继承HibernateDaoSupport实现一个DAO。
	3. 在AOP支持的事务中装配。

48. Spring支持的事务管理类型

	Spring支持两种类型的事务管理：
	
	1. 编程式事务管理：这意味你通过编程的方式管理事务，给你带来极大的灵活性，但是难维护。
	2. 声明式事务管理：这意味着你可以将业务代码和事务管理分离，你只需用注解和XML配置来管理事务。

49. Spring框架的事务管理有哪些优点？

	它为不同的事务API  如 JTA，JDBC，Hibernate，JPA 和JDO，提供一个不变的编程模式。
	它为编程式事务管理提供了一套简单的API而不是一些复杂的事务API如
	它支持声明式事务管理。
	它和Spring各种数据访问抽象层很好得集成。

50. 你更倾向用那种事务管理类型？

	大多数Spring框架的用户选择声明式事务管理，因为它对应用代码的影响最小，因此更符合一个无侵入的轻量级容器的思想。声明式事务管理要优于编程式事务管理，虽然比编程式事务管理（这种方式允许你通过代码控制事务）少了一点灵活性。

### Spring面向切面编程（AOP）

51. 解释AOP

	面向切面的编程，或AOP， 是一种编程技术，允许程序模块化横向切割关注点，或横切典型的责任划分，如日志和事务管理。

52. Aspect 切面

	AOP核心就是切面，它将多个类的通用行为封装成可重用的模块，该模块含有一组API提供横切功能。比如，一个日志模块可以被称作日志的AOP切面。根据需求的不同，一个应用程序可以有若干切面。在Spring AOP中，切面通过带有@Aspect注解的类实现。

52. 在Spring AOP 中，关注点和横切关注的区别是什么？

	关注点是应用中一个模块的行为，一个关注点可能会被定义成一个我们想实现的一个功能。
横切关注点是一个关注点，此关注点是整个应用都会使用的功能，并影响整个应用，比如日志，安全和数据传输，几乎应用的每个模块都需要的功能。因此这些都属于横切关注点。

54. 连接点

	连接点代表一个应用程序的某个位置，在这个位置我们可以插入一个AOP切面，它实际上是个应用程序执行Spring AOP的位置。

55. 通知

	通知是个在方法执行前或执行后要做的动作，实际上是程序执行时要通过SpringAOP框架触发的代码段。

	Spring切面可以应用五种类型的通知：

	* before：前置通知，在一个方法执行前被调用。
	* after: 在方法执行之后调用的通知，无论方法执行是否成功。
	* after-returning: 仅当方法成功完成后执行的通知。
	* after-throwing: 在方法抛出异常退出时执行的通知。
	* around: 在方法执行之前和之后调用的通知。

56. 切点

	切入点是一个或一组连接点，通知将在这些位置执行。可以通过表达式或匹配的方式指明切入点。

57. 什么是引入? 

	引入允许我们在已存在的类中增加新的方法和属性。

58. 什么是目标对象? 

	被一个或者多个切面所通知的对象。它通常是一个代理对象。也指被通知（advised）对象。

59. 什么是代理?

	代理是通知目标对象后创建的对象。从客户端的角度看，代理对象和目标对象是一样的。

60. 有几种不同类型的自动代理？

	* BeanNameAutoProxyCreator
	* DefaultAdvisorAutoProxyCreator
	* Metadata autoproxying

61. 什么是织入。什么是织入应用的不同点？

	织入是将切面和到其他应用类型或对象连接或创建一个被通知对象的过程。

	织入可以在编译时，加载时，或运行时完成。

62. 解释基于XML Schema方式的切面实现。

	在这种情况下，切面由常规类以及基于XML的配置实现。

63. 解释基于注解的切面实现

	在这种情况下(基于@AspectJ的实现)，涉及到的切面声明的风格与带有java5标注的普通java类一致。

### Spring的MVC

64. 什么是Spring的MVC框架？

	Spring 配备构建Web 应用的全功能MVC框架。Spring可以很便捷地和其他MVC框架集成，如Struts，Spring 的MVC框架用控制反转把业务对象和控制逻辑清晰地隔离。它也允许以声明的方式把请求参数和业务对象绑定。

65. DispatcherServlet

	Spring的MVC框架是围绕DispatcherServlet来设计的，它用来处理所有的HTTP请求和响应。

66. WebApplicationContext

	WebApplicationContext 继承了ApplicationContext  并增加了一些WEB应用必备的特有功能，它不同于一般的ApplicationContext ，因为它能处理主题，并找到被关联的servlet。

67. 什么是Spring MVC框架的控制器？

	控制器提供一个访问应用程序的行为，此行为通常通过服务接口实现。控制器解析用户输入并将其转换为一个由视图呈现给用户的模型。Spring用一个非常抽象的方式实现了一个控制层，允许用户创建多种用途的控制器。

68. @Controller 注解

	该注解表明该类扮演控制器的角色，Spring不需要你继承任何其他控制器基类或引用Servlet API。

69. @RequestMapping 注解

	该注解是用来映射一个URL到一个类或一个特定的方处理法上。
	
70. spring AOP的原理
	
### 其它框架

1. hibernate和iBatis的区别

2. 讲讲MyBatis的连接池

3. hibernate中的1级和2级缓存的使用方式以及区别原理（Lazy-Load的理解）

4. Hibernate的原理体系架构，五大核心接口，Hibernate对象的三种状态转换，事务管理。