# Spring

### 1. Spring Projects

1. **Spring IO** - платформа для построения приложений, предоставляющая набор зависимостей, при этом давая разработчикам полный контроль над деплоем только тех из них, которые им нужны. <sup>[\[1.1\]][1.1]</sup>
  - Проект является 100% с открытым кодом.
  - Одна платформа, множество возможностей: веб, интеграционные, серийные, реактивные, big data приложения.
  - Упрощенная разработка в связке с Spring Boot.
  - Готовые к продакшену решения "из коробки".
  - Зависим только от Java SE, поддерживает Groovy, Grails и немного Java EE.
  - Работает с существующими инструментами управления зависимостями, такими как Maven или Gradle.
  - Работает на Java 1.7+

2. **Spring Boot** - генерация средств упрощения процесса конфигурации Spring приложений. Он не является средством автоматической генерации кода, а представляет собой плагин для системы автоматизации сборки проектов. <sup>[\[1.2\]][1.2]</sup>
  - Плагин предоставляет возможности для тестирования и разворачивания Spring приложения.
  - Предоставляет встроенный Tomcat, Jetty или Undertow (на выбор), отпадает необходимость в деполе WAR файлов.
  - Работает с существующими инструментами управления зависимостями, такими как Maven или Gradle.
  - Предоставляет готовый pom.xml файл для Maven.
  - Конфигурирование ресурсов исходя из содержания classpath.
  - Отпадает необходимость в настройке конфигураций в коде или через .xml файлы.

3. **Spring Framework** - обеспечивает базовую поддержку управления зависимостями, управление транзакциями веб-приложений, доступ к данным, обмен сообщениями и многое другое. <sup>[\[1.3\]][1.3]</sup>
  - DI.
  - AOP, включая декларативное управления транзакциями.
  - Создание Spring MVC веб-приложений и RESTful веб-сервисов.
  - Начальная поддержка JDBC, JPA, JMS.
  - Работает на Java 1.5+ (3.х), Java 1.6+ (4.x).

4. **Spring Web Services** - нацелен на облегчения разработки SOAP-сервиса методом contract-airst, позволяя создавать легкоизменяемые веб-сервисы путем конфигурации XML-настроек. <sup>[\[1.4\]][1.4]</sup>
  - Основан на Spring Framework, а значит поддерживает DI.
  - Включает в себя такие методологии, как WS-I basic profile, contract-airst, имеет слабую связь между контрактом и реализацией.
  - Мощный маппинг: распределение XML-запросов по объектам в зависимости от сообщения, SOAP Action заголовка или XPath выражения.
  - Поддержка XML API: входящие XML-сообщения могут быть обработаны стандартным JAXP API, например, DOM, SAX, StAX, а также JDOM, dom4j, XOM или другими подобными инструментами.
  - Гибкое XML размещение: Object/XML маппинг модуль поддерживает JAXB 1, 2, Castor, XML Beans, JiBX и XStream. И так как это отдельный модуль, то вы можете использовать его и не в веб-сервисах.
  - Поддержка WS-Security.
  - Сборка с помощью Maven.

5. **Spring Data** - упрощает использование таких технологий доступа к данным, как реляционные и нереляционные СУБД, map-reduce фреймворки и облачные сервисы. Spring Data состоит из подпроектов для конкретной СУБД. Эти проекты разработаны множеством компаниями и разработчиками, которые стоят за этими технологиями. <sup>[\[1.5\]][1.5]</sup>
  - __Spring Data JPA__ упрощает разработку JPA-приложений. Этот модуль расширяет поддержку JPA-слоя доступа к данным, а также облегчает разработку Spring-приложений, использующих технологии доступа к данным. <sup>[\[1.6\]][1.6]</sup>
  - __Spring Data MongoDB__ - предоставление совместимой и похожей на Spring модели программирования для данной СУБД, сохраняя её возможности и функциональность. <sup>[\[1.7\]][1.7]</sup>
  - __Spring Data Redis__ - предоставляет простое кофигурирование и доступ к Redis из Spring-приложений, а также предлагает низко и высокоуровневые абстракции для взаимодействия с СУБД избавление пользователя от инфраструктурных проблем. <sup>[\[1.8\]][1.8]</sup>
  - __Spring for Apache Hadoop__ - упрощает использование Apache Hadoop, предоставляя унифицированную модель конфигурирования и простое в использование API для HDFS, MapReduce, Pig и Hive. <sup>[\[1.9\]][1.9]</sup>
  - __Spring Data GemFire__ - облегчение создания высокомасштабируемых Spring-приложений, используя Pivotal GemFire как платформу распределения данных. <sup>[\[1.10\]][1.10]</sup>
  - __Spring Data REST__ позволяет обращаться к JPA-репозиториям как к REST-сервисам. <sup>[\[1.11\]][1.11]</sup>
  - __Spring Data JDBC Extensions__ - это часть проекта Spring Data. Поддержка JDBC в Spring Framework обширна и охватывает наиболее часто используемые функции. Это расширение проекта предоставляет поддержку для работы с некоторыми возможностями СУБД Oracle, а также с новыми случаями использования, такими как типобезопасные запросы с использованием Querydsl. <sup>[\[1.12\]][1.12]</sup>
  
***

### 2. Spring Framework

1. **Spring Framework** — обесепечивает решения многих задач, с которыми сталкиваются java-разработчики и организации, которые хотят создать информационную систему, основанную на платформе Java. Наиболее известен как источник расширений, нужных для эффективной разработки сложных бизнес-приложений вне тяжеловесных программных моделей, которые исторически были доминирующими в промышленности.

2. **IoC (Inversion of Control)** — паттерн для передачи контроля за создание объектов контейнеру.

3. **Dependency Injection (DI)** — процесс предоставления внешней зависимости программному компоненту. Является одним из примеров IoC.

4. **IoC Container** отвечает за инстанцирование, конфигурирование и сборку объектов. IoC контейнер получает информацию из XML файла и с ним же работает. Существует два типа IoC конейнеров: `BeanFactory` и `ApplicationContext`.

5. **BeanFactory Container** - простейший контейнер, предоставляющий базовую поддержку для DI.
  - Пример инициализации:
  ```Java
  Resource resource = new ClassPathResource("applicationContext.xml");  
  BeanFactory factory = new XmlBeanFactory(resource);  
  ```
  
6. **ApplicationContext Container** - этот контейнер добавляет интерпрайз функциональность поверх BeanFactory контейнера..
  - Пример инициализации:
  ```Java
  ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");  
  ```
  
7. **AOP (Aspect Oriented Programmin)** - парадигма программирования, основанная на идее разделения функциональности для улучшения разбиения программы на модули.

8. **SpEL (Spring Expression Language)** - мощный язык для выполнения запросов и манипуляций с графом объектов во время рантайма. 

9. **Spring Framework Runtime** <sup>[\[2.1\]][2.1]</sup>
  ![Spring Framweork Runtime](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/images/spring-overview.png)

10. **Core Container** <sup>[\[2.2\]][2.2]</sup>
  - `spring-core` - модуль, предоставляющий основные части фреймворка, включая IoC и DI особенности.
  - `spring-bean` - модуль, предоставляющий `BeanFactory` контейнер, который представляет собой реализацию паттерна фабрики.
  - `spring-context` - модуль, предоставляющий `ApplicationContext` контейнер, построенный на основе Core и Beans модулей, который является посредником при получении доступа к любому объекту.
  - `spring-expression` - модуль, предоставляющий мощный язык Expression Language для выполнения запросов и манипуляций с графом объектов во время рантайма.

11. **AOP and Instrumentation** <sup>[\[2.3\]][2.3]</sup>
  - `spring-instrument` - обеспечивает поддержку инструментария классов и реализации classloader, которые могут использоваться в некоторых серверных приложениях.
  - `spring-aop` - предоставляет реализацию аспектно-ориентированного программирования, позволяющую вам определять, например, перехватчиков методов и pointcuts, чтобы чистенько разъединить код, который реализует различную функциональность.
  - `spring-aspects` - модуль, предоставляющий интеграцию с AspectJ, который является мощным AOP фреймворком.
  - `spring-instrument-tomcat` - модуль, содержащий спринговский инструментарий для Tomcat.

12. **Messaging** <sup>[\[2.4\]][2.4]</sup>
  - `spring-messaging` - модуль, предоставляющий абстракции из Spring Integration проекта, такие как `Message`, `MessageChannel`, `MessageHandler` и другие. Они служат основой для messaging-based приложений. Он также включает в себя набор аннотаций для маппинга сообщений в методы.

13. **Data Access/Integration** <sup>[\[2.5\]][2.5]</sup>
  - `spring-jdbc` - модуль, предоставляющий уровень JDBC-абстракции, который освобождает от утомительного кодинга JDBC аспектов.
  - `spring-orm` - модуль, предоставляющий интеграционные уровни для популярных объекто-ориентированных mapping API, включая JPA, JDO, Hibernate, iBatis.
  - `spring-oxm` -  модуль, предоставляющий уровень абстракции, который поддерживает Object/XML mapping реализации для JAXB, Castor, XMLBeans, JiBX и XStream. 
  - `spring-jms` - модуль, содержащий фичи для создания и использования сообщений. Начиная с 4.1 версии фреймворка, он предоставляет интеграцию с `spring-messaging` модулем.
  - `spring-tx` - модуль, поддерживающий программное и декларативное транзакционное управления для всех POJO и классов, которые реализуют специальные интерфейсы.

14. **Web** <sup>[\[2.6\]][2.6]</sup>
  - `spring-web` - модуль, предоставляющий базовые web-ориентированые интеграционные фичи, такие как multipart file-upload функциональность и инициализация IoC контейнера используя листнеры и web-ориентированные context модули приложения.
  - `spring-webmvc` - модуль (также известный, как Web-Servlet модуль), содержащий Spring MVC и REST Web Services реализацию для веб приложений.
  - `spring-websocket` - модуль , предоставляющий поддержку для WebSocket-based приложений, для двусторонних коммуникаций между клиентами и для серверов в веб приложениях.
  - `spring-webmvc-portlet` - модуль (также известный, как Web-Portlet модуль), предоставляющий функциональность Web-Servlet модуля, а также MVC реализацию для использования в Portlet среде. Отражает функциональность `spring-webmvc` модуля.

15. **Test** <sup>[\[2.7\]][2.7]</sup>
  - `spring-test` - модуль, поддерживающий тестирование Spring компонентов с использованием JUnit или TestNG фреймворков.

16. **Dependency Management** - процесс, включающий в себя распределение в проекте всех библиотек завимимостей в виде jar файлов, их хранение и добавление в classpaths. <sup>[\[2.8\]][2.8]</sup>
  - Зависимости могут быть прямыми (например приложение зависит напрямую от Spring runtime) или косвенными (например приложение зависит от `common-dbcp`, который зависит от `commons-pool`).
  - Косвенные зависимости также известны как "транзитивные", и они являются наиболее сложными для идентификации и управления.

17. **Maven "Bill Of Materials" Dependency** - чтобы не произошло путанницы или ошибок с версиями спринговских jar зависимостей при использовании мавена, существует концепция - "bill of materials" (BOM) зависимость. <sup>[\[2.9\]][2.9]</sup>
  - Для того, чтобы убедиться, что все спринговские зависимости одинаковой версии, стоит импортировать `spring-framework-bom` зависимость. После этого отпадает необходимость писать `<version>` в зависимостях спринга.

18. **JCL (Jakarta Commons Logging) API** - обязательная зависимость логгирования в спринге.
  - `commons-logging` - модуль, зависимый от `spring-core` модуля, реализует JCL `Log` объекты. Он заставляет все прочие модули зависить от себя во время компиляции. <sup>[\[2.10\]][2.10]</sup>
  - Этот модуль обладает runtime алгоритмом обнаружения в classpath других фрейморков логгирования и используется один из них, который считает наиболее подходящим (хотя можно настроить, чтобы выбирать самому).
  - Т.к. этот модуль уже устарел, но заменить его возможности не представляется, то единственным способом исключить этот API из фреймворка, это исключить его из `spring-core` модуля. <sup>[\[2.11\]][2.11]</sup>

19. **SLF4J (Simple Logging Facade for Java)** - лучше, чем `commons-logging` и эффективнее в рантайме, потому что использует время компиляции для привязок, вместо того, чтобы юзать runtime поиск. <sup>[\[2.12\]][2.12]</sup>
  - SLF4J предоставляет привязки для многих стандартных фреймворков логгирования, включая JCL.
  - Обычно к SLF4J присоединяют Spring, а затем предоставляют явное связывание из SLF4J в Log4J.

***

### 3. IoC container

***

### 4. Resources

1. **`Resource`** - интерфейс, предназначенный для абстракции доступа к низкоуровневым ресурсам. <sup>[\[4.1\]][4.1]</sup>
  ```Java
  public interface InputStreamSource {
    InputStream getInputStream() throws IOException;
  }

  public interface Resource extends InputStreamSource {
    boolean exists();
    boolean isOpen();
    URL getURL() throws IOException;
    File getFile() throws IOException;
    Resource createRelative(String relativePath) throws IOException;
    String getFilename();
    String getDescription();
  }
  ```
  - `getInputStream()` - находит и открывает ресурс, возвращая `InputStream` для чтения из ресурса.
  - `exists()` - проверяет, если ресурс существует физически или нет.
  - `isOpen()` - проверяет, если ресурс представляет хендл с открытым стримом.
  - `getDescription()` - возвращает описание для данного ресурса. Используется для вывода ошибок при работе с ресурсом.

2. **`UrlResource`** служит оберткой для `java.net.URL`, и может быть использован для доступа к любому объекту, который доступен по URL, например файлы, HTTP ссылка, FTP ссылка и т.д. <sup>[\[4.2\]][4.2]</sup>
3. **`ClassPathResource`** - реализация `Resource`, которая поддерживает разрешения `java.io.File`. Ресурс был создан Java кодом явно используя конструктор, но постоянно будет создаваться неявно, когда вы будете вызывать API метод, который принимает путь аргументом в виде строки. <sup>[\[4.3\]][4.3]</sup>
4. **`FileSystemResource`** - реализация `Resource` для `java.io.File` хэндлеров. Поддерживает разрешения из `File` и из `URL`. <sup>[\[4.4\]][4.4]</sup>
5. **`ServletContextResource`** - реализация `Resource` для `java.io.File` хэндлеров. Поддерживает разрешения из `File` и из `URL`. <sup>[\[4.5\]][4.5]</sup>
6. **`InputStreamResource`** - реализация `Resource` для заданного `InputStream`. Она должна быть использована только в случае, если нет подходящей реализации для `Resource`. <sup>[\[4.6\]][4.6]</sup>
  - В отличии от других реализаций `Resource`, эта является дескрипторои для уже открытого ресурса, поэтому всегда метод `isOpen()` этого класса возвращает true.
7. **`ByteArrayResource`** - реализация `Resource` для заданного массива байт. Она создает `ByteArrayInputStream` для этого массива. <sup>[\[4.7\]][4.7]</sup>
  - Эффективна для загрузки содержимого из любого массива байтов, не прибегая к использованию одноразового `InputStreamResource`.
8. **`ResourceLoader`** - интерфейс, предназначенный для объектов, которые могут возвращать (т.е. загружать) `Resource` инстансы. <sup>[\[4.8\]][4.8]</sup>
  ```Java
  public interface ResourceLoader {
    Resource getResource(String location);
  }
  ```
  - Все контексты приложений реализуют этот интерфейс, следовательно все контексты приложений могут получать `Resource` инстансы.
  - Примеры загрузки ресурсов:
  ```Java
  Resource template = ctx.getResource("some/resource/path/myTemplate.txt");
  Resource template = ctx.getResource("classpath:some/resource/path/myTemplate.txt");
  Resource template = ctx.getResource("file:///some/resource/path/myTemplate.txt");
  Resource template = ctx.getResource("http://myhost.com/resource/path/myTemplate.txt");
  ```
  - Первый ресурс загружается из classpath, второй через URL из файловой системы, третий через URL, четвертый зависит от `AppliacationContext` реализации.
  
9. **`ResourceLoaderAware`** - специальный указательный интерфейс, иденцифицирующий объекты, которые ожидают реализации `ResourceLoader`. <sup>[\[4.9\]][4.9]</sup>
  ```Java
  public interface ResourceLoaderAware {
    void setResourceLoader(ResourceLoader resourceLoader);
  }
  ```
  - Когда класс реализует этот интерфейс и деплоится в контекст приложения (как спринговский бин), он распознается им, как `ResourceLoaderAware`. Этот контекст затем вызовет `setResourceLoader(ResourceLoader)`, предоставляя методу себя, как аргумент.

10. **Resources as dependencies** - если бин обладает свойством типа `Resource`, он может быть сконфигурирован с помощью простой строки для этого ресурса. <sup>[\[4.10\]][4.10]</sup> Например: 
  ```Xml
  <bean id="myBean" class="...">
    <property name="template" value="some/resource/path/myTemplate.txt"/>
    <property name="template" value="classpath:some/resource/path/myTemplate.txt">
    <property name="template" value="file:///some/resource/path/myTemplate.txt"/>
  </bean>
  ```
  - Важно заметить, что путь к первому ресурсу не обладает префиксом, поэтому каким способом будет загружен ресурс зависит от типа контекста (`ClassPathResource`, `FileSystemResource` или `ServletContextResource`).

11. **Constructing application contexts** - конструктор контекста приложения обычно принимает строку или массив строк в качестве пути к ресурсу, как например к XML файлу, который составляет определение конекста. <sup>[\[4.11\]][4.11]</sup>
  - Ниже представлены примеры создания контекста приложения:
  ```Java
  ApplicationContext ctx = new ClassPathXmlApplicationContext("conf/appContext.xml");
  ```
  - Определения бина будут загружены из classpath, так как будет использован `ClassPathResource`. Но если создать `FileSystemXmlApplicationContext` следующим образом:
  ```Java
  ApplicationContext ctx = new FileSystemXmlApplicationContext("conf/appContext.xml");
  ```
  - Определение бина будет загружено из файловой системы, в данном случае относительно текущей рабочей директории.
  ```Java
  ApplicationContext ctx = new FileSystemXmlApplicationContext("classpath:conf/appContext.xml");
  ```
  - В этом случае контекст загрузит определение бина из classpath, однако он останется `FileSystemXmlApplicationContext`, хотя и перезапишет дефолтный тип `Resource`, созданного для загрузки бина.
  ```Java
  ApplicationContext ctx = new ClassPathXmlApplicationContext(
    new String[] {"services.xml", "daos.xml"}, MessengerService.class);
  ```
  - Здесь `ClassPathXmlApplicationContext` инстанс состоит из нескольких определений бинов, указанный в service.xml и daos.xml. <sup>[\[4.12\]][4.12]</sup>
  ```Java
  ApplicationContext ctx =
    new ClassPathXmlApplicationContext("classpath*:conf/appContext.xml");
  ```
  - В данном примере демонстрируется использование вайлдкардов, для загрузки нескольких classpath ресурсов и слияния их всех в один контекст приложения. <sup>[\[4.13\]][4.13]</sup>
  ```Java
  ApplicationContext ctx =
    new FileSystemXmlApplicationContext("file:///conf/context.xml");
  ```
  - Так как любой путь восприниматься как относительный (`FileSystemApplicationContext` заставляет все привязанные к `FileSystemResource` инстансы воспринимать пути как относитенльные, не важно со слешем они или без), то настоящий абсолютный путь будет записываться с помощью префикса `file`. <sup>[\[4.14\]][4.14]</sup>
  
***

### 5. Validation, Data Binding, and Type Conversion

***

### 6. SpEL

***

### 7. AOP

1. **AOP (Aspect Oriented Programming)** - АОП - парадигма программирования, основанная на идее разделения функциональности для улучшения разбиения программы на модули. В то время, как в ООП главной чертой модульности является класс, в АОП - это аспект.
  - АОП фреймворк является одним из ключевых компонентов спринга, хоть IoC контейнер и не зависит от него.
  - АОП используется для следующих целей:
    + Предоставить декларативные корпоративные сервисы, в частности заменяя EJB декларативные сервисы. Один из этих сервисов является declarative transaction management.
    + Позволяет пользователям реализовывать свои аспекты, дополняя ООП АОП-ом.

2. **Aspect** - Аспект - набор задач, разделенных между множеством классов. Управление транзакциями является хорошим примером разделения задачи в корпоративных Java приложениях. 
   - В АОП фреймворке аспекты реализуются при помощи регулярных классов или классов, аннотированных @Aspect аннотацией.

3. **Join point** - Точка входа - всегда представляет собой выполнение метода.

4. **Advice** - Совет - событие, выполненное одним из аспектов в конкретной точке входа.
  - Существует несколько типов советов:
    + Before - совет, который выполняется перед точкой входа, но не может остановить дальнейшее выполнение метода, обозначенного этой точкой.
    + After returning - совет, который выполняется после return (если не было выкинуто исключение).
    + After throwing - совет, который выполняется после выкидывания исключения.
    + After (finally) - совет, который выполняется в любом случае после выполнения метода.
    + Around - совет, который оборачивает точку входа (как например при вызове метода). Он по сути является самым мощным советом, т.к. контролирует вход и выход в точку входа.
  - Многие АОП фреймворки, включая спринг, принимают совет как перехватчика, контролирующего цепочку перехватчиков вокруг точки входа.

5. **Introduction** - Представление - объявляет дополнительные методы или поля в зависимости от типа.
  - АОП спринга позволяет предоставлять новые интерфейсы (и соответствующую реализацию) для любого объекта совета.

6. **Target object** - Целевой объект - объект, который является советом для одного или более аспектов.

7. **AOP proxy** - АОП прокси - объект, созданный АОП фреймворком для реализации контрактов аспектов (выполнение метода совета и типо того).
   - В спринге, АОП прокси является JDK dynamic proxy или CGLIB proxy.

8. **Weaving** - Связывание - связывание аспектов с типами или объектами приложения для создания объекта аспекта.
  - Это может быть сделано во время компиляции, загрузки или выполнения. АОП спринга, как и другие Java АОП фреймворки производит связывание во время выполнения.


***

### 8. Spring AOP APIs

***

### 9. Unit Testing

***

### 10. Integration Testing

***

### 11. Transaction Management

***

### 12. DAO

***

### 13. JDBC

***

### 14. ORM

***

### 15. O/X Mappers

***

### 16. Web MVC

***

### 17. View technologies

***

### 18. Integrating with other web frameworks

***

### 19. Portlet MVC

***

### 20. WebSocket

***

### 21. CORS

***

### 22. Web Services

***

### 23. EJB

***

### 24. JMS

***

### 25. JCA CCI

***

### 26. Email

***

### 27. Task Execution and Scheduling

***

### 28. Dynamic language support

***

### 29. Cache Abstraction

***

### 30. Classic Spring Usage

***

### 31. Classic Spring AOP Usage

***

### 32. XML Schema-based configuration

***

### 33. Extensible XML authoring

***

### 34. Spring REST



[1.1]: http://platform.spring.io/platform/
[1.2]: http://projects.spring.io/spring-boot/
[1.3]: http://projects.spring.io/spring-framework/
[1.4]: http://projects.spring.io/spring-ws/
[1.5]: http://projects.spring.io/spring-data/
[1.6]: http://projects.spring.io/spring-data-jpa/
[1.7]: http://projects.spring.io/spring-data-mongodb/
[1.8]: http://projects.spring.io/spring-data-redis/
[1.9]: http://projects.spring.io/spring-hadoop/
[1.10]: http://projects.spring.io/spring-data-gemfire/
[1.11]: http://projects.spring.io/spring-data-rest/
[1.12]: http://projects.spring.io/spring-data-jdbc-ext/

[2.1]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-modules
[2.2]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-core-container
[2.3]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-aop-instrumentation
[2.4]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-messaging
[2.5]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-data-access
[2.6]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-web
[2.7]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-testing
[2.8]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#dependency-management
[2.9]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-maven-bom
[2.10]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-logging
[2.11]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-not-using-commons-logging
[2.12]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#overview-logging-slf4j

[4.1]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-resource
[4.2]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-implementations-urlresource
[4.3]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-implementations-classpathresource
[4.4]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-implementations-filesystemresource
[4.5]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-implementations-servletcontextresource
[4.6]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-implementations-inputstreamresource
[4.7]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-implementations-bytearrayresource
[4.8]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-resourceloader
[4.9]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-resourceloaderaware
[4.10]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-as-dependencies
[4.11]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-app-ctx-construction
[4.12]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-app-ctx-classpathxml
[4.13]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-classpath-wildcards
[4.14]: http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#resources-filesystemresource-caveats

