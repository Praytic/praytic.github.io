# Web Service

### 1. Общее

1. **Web Service** - приложение, предназначенное для обеспечения сетевого взаимодействия между компьютерами. 
   - Сервис доступен по сети, может располагаться и выполняться на разных компьютерах. 
   - Передача сообщений между сервисом и клиентом происходит в независимом формате.
   - Web Service может быть создан из существующего Web приложения.
   - Сервис использует стандартизированную XML messaging систему.
   - Не привязан к операционной системе или языку программирования

2. **Переиспользуемые компоненты** - веб сервисы могут предоставить приложению такие компоненты, как: обмен валюты, 
сводка о погоде, перевод текста и т.д. 

3. **Подключение сторонних программ** - веб сервисы могут обмениваться данными с различными программами независимо от
 языка программирования, на котором они написаны.

4. **Service** - реализация веб сервиса. <sup>[\[1\]][service]</sup>
   - Сервис может быть маленьким, что будет умещаться в один JS файл, а может быть детально проработанным 30-летним COBOL приложением, запускаемым на центральном процессоре.

5. **Service Description** - интерфейс веб сервиса. <sup>[\[1\]][service-description]</sup>
   - Он выражается через XML и обуславливается одним или более стандартами.

6. **Service Platform** - среда, используемая для хостинга одного или более веб сервисов. <sup>[\[1\]][service-platform]</sup>
   - Она включает в себя один или более SOAP серверов, ни одного или несколько UDDI реестров, защиту и транзакционные сервисы, используемые веб сервисами, которые хостятся на ней, и прочую инфраструктуру.
 
7. **Service Provider** - провайдер веб сервиса, который реализует его и делает доступным в интернете. <sup>[\[1\]][service-provider]</sup>
   - Провайдер может полностью предоставлять платформу или же только некоторые части J2EE функциональности, включая немного веб сервисвисных аддонов.

8. **Service Requestor** - логика, которая находит и внедряет программные средства, предоставляемые одним или более провайдерами. <sup>[\[1\]][service-requestor]</sup>
   - Роль реквестора могут играть: человек, использующий веб сервис, или другой веб сервис.

9. **Service Registry (Broker)** - логически-централизованная директория сервисов, куда девелоперы публикуют новые 
сервисы и где можно найти существующие. Поэтому этот элемент является координационным центром для компаний и их услуг. <sup>[\[1\]][service-registry]</sup>
   - Реестр предоставляет следующего вида информацию: бизнес данные, такие как имя, описание, контактная информация, или данные, необходимые для использования веб сервиса.
 
10. Пример веб сервиса: [dailyinfo](http://www.cbr.ru/dailyinfowebserv/dailyinfo.asmx) 

***

### 2. Основные компоненты

1. **SOAP (Simple Object Access Protocol)** - основанный на XML протокол обмена сообщениями.

2. **WSDL (Web Services Description Language)** - язык разметки, основанный на XML, преднзначенный для 
описания веб сервисов.

3. **UDDI (Universal Description, Discovery, and Integration)** - предоставляет всемирный реестр веб сервисов для рекламы, поиска и хранения.

4. Диаграмма взаимодействия между SOAP, WSDL и UDDI: <sup>[\[2\]][2.diagram]</sup>
   ![Взаимодействие между SOAP, WSDL и UDDI](https://dl.dropboxusercontent.com/1/view/6hznyqne2o82ndg/Apps/Shutter/Selection_036.png)
   - Приложение играет роль веб сервисов, которые нужны клиенту для доступа к другому приложению или бизнес логике, расположенной где-то в сети. 
   - Клиент делает запрос в UDDI реестр для нахождения сервиса по имени, категории, идентификатору или какой-то другой спецификации. 
   - Как только сервис найден, клиент получает информацию о местонахождении WSDL документа из UDDI реестра. 
   - WSDL документ содержит информацию о том, как обратиться к веб сервису, и формат запросов в XML схему.
   - Клиент создает SOAP сообщение в соответствии с XML схемой, взятой из WSDL, и посылает запрос хосту (где находится веб сервис).

***

### 3. SOAP

1. **SOAP** - протокол обмена структурированными сообщениями в распределенной вычислительной среде. Также предоставляет стандарт структуры упаковки данных для транспортировки XML документов с помощью различных интернет-технологий, как: SMTP, HTTP, FTP. <sup>[\[3\]][soap]</sup>
    - Так как SOAP обладает стандартным механизмом транспортировки, различные клиенты и серверы могут взаимодействовать, например, с EJB через .NET клиент и наоборот.

2. Пример взаимодействия клиента с Web приложением (регистрация аккаунта):
    - Программа на клиентской стороне конвертирует информацию о регистрации аккаунта в SOAP сообщение.
    - SOAP сообщение отсылается в веб сервис, как тело HTTP POST запроса.
    - Веб сервис распаковывает SOAP реквест и конвертирует в комманду, которую понимает приложение на сервере.
    - Приложение обрабатывает информацию своей логикой и отправляет ответ с новым уникальным номером аккаунта.
    - Следующим шагом, веб сервис конвертирует ответ сервера в SOAP сообщение, которое отправляет назад в клиентское 
    приложение, как ответ на HTTP запрос.
    - Клиентское приложение распаковывает SOAP сообщение и предоставляет клиенту соотвествующую информацию.

3. Клиент/сервер связь:
   ```
                  HTTP POST of SOAP request document
     SOAP: client ----------------------------------> service

           client <---------------------------------- service
	                   SOAP (maybe JSON) document
   ```

4. **SOAP Building Blocks**. SOAP сообщение - это обычный XML документ, содержащий следующие элементы:
	- Оболочка - идентифицирует XML документ как SOAP сообщение.
	- Заголовок - содержит различного рода информацию о сообщении, которая помещается обычно в заголовки.
	- Тело - содержит информацию о вызове и ответе.
	- Ошибка - содержит все ошибки и текущий статус.

***

### 4. WSDL

1. **WSDL (Web Service Description Language)** - XML технология, которая описывает интерфейс веб сервиса в стандартизированном виде. WSDL указывает стандарт, как веб сервис должен представлять входные и выходные параметры при вызове извне, как должна выглядеть структура функции, природа вызова и как осуществлять связывание протокола сервера. <sup>[\[4\]][wsdl]</sup>
   - WSDL позволяет различным клиентам автоматически распознавать, как взаимодействовать с веб сервисом.

1. **WSDL документ** - описывает веб сервис. Он указывает местоположение сервиса и его методы, используя следующие элементы:
    - `<types>` - определяет типы данных, используемые веб сервисом.
    - `<message>` - определяет элементы данных для каждой операции.
    - `<portType>` - описывает операции и сообщение, которые могут встретиться в сервисе.
    - `<binding>` - определяет протокол и формат данных для каждого типа порта.
    - `<service>` - определяет адрес веб сервиса.
    - `<definition>` - корневой элемент каждого WSDL документа.
    - `<operation>` - абстрактное определение операции для сообщения.
    - `<documentation>` - предоставляет документацию
    - `<import>` - импортирует сторонние WSDL документы или XML Schemas.
    
2. **Структура WSDL документа** выглядит следующим образом:
    ```xml
    <definitions>
        <types>
          data type definitions........
        </types>
        <message>
          definition of the data being communicated....
        </message>
        <portType>
          set of operations......
        </portType>
        <binding>
          protocol and data format specification....
        </binding>
    </definitions> 
   ```

3. `<portType>` - элемент, который определяет веб сервис, операции, приводимые в нем, и задействованные сообщения.
    - __request-response__ - самый распространенный тип операции. Она получает запрос и возвращает ответ.
    - __one-way__ - операция может получать сообщения, но не будет возвращать ответ.
    - __solicit-response__ - операция может отправлять запрос и будет ждать ответа.
    - __notification__ - операция может посылать сообщений, но не будет ждать ответа.
    
4. Пример Request-Response операции (словарь терминов):
   ```xml
    <message name="getTermRequest">
      <part name="term" type="xs:string"/>
    </message>
    <message name="getTermResponse">
      <part name="value" type="xs:string"/>
    </message>
    <portType name="glossaryTerms">
      <operation name="getTerm">
        <input message="getTermRequest"/>
        <output message="getTermResponse"/>
      </operation>
    </portType> 
      ```
    - `<portType>` определяет "glossaryTerms" как имя порта, а `getTerm` - имя операции
    - `<message>` элементы определяют `<part>` сообщений "getTermRequest" и "getTermResponse".
      
5. Пример One-Way операции (словарь терминов):
   ```xml
    <message name="newTermValues">
      <part name="term" type="xs:string"/>
      <part name="value" type="xs:string"/>
    </message>
    <portType name="glossaryTerms">
      <operation name="setTerm">
        <input name="newTerm" message="newTermValues"/>
      </operation>
    </portType > 
   ```
   - В этом примере "glossaryTerms" определяет one-way операцию "setTerm".
   - "setTerm" операция позволяет вводить новое сообщение используя "newTermValues".
   
6. Пример WSDL файла:
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <definitions name="HelloService"
                 targetNamespace="http://www.ecerami.com/wsdl/HelloService.wsdl"
                 xmlns="http://schemas.xmlsoap.org/wsdl/"
                 xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
                 xmlns:tns="http://www.ecerami.com/wsdl/HelloService.wsdl"
                 xmlns:xsd="http://www.w3.org/2001/XMLSchema">
        <types>
            <xsd:schema>
                <xsd:import
                        schemaLocation="http://localhost:9876/ts?xsd=1"
                        namespace="http://ts.ch02/">
                </xsd:import>
            </xsd:schema>
        </types>
        <message name="SayHelloRequest">
            <part name="firstName" type="xsd:string"/>
        </message>
        <message name="SayHelloResponse">
            <part name="greeting" type="xsd:string"/>
        </message>
        <portType name="Hello_PortType">
            <operation name="sayHello">
                <input message="tns:SayHelloRequest"/>
                <output message="tns:SayHelloResponse"/>
            </operation>
        </portType>
        <binding name="Hello_Binding" type="tns:Hello_PortType">
            <soap:binding style="rpc"
                          transport="http://schemas.xmlsoap.org/soap/http"/>
            <operation name="sayHello">
                <soap:operation soapAction="sayHello"/>
                <input>
                <soap:body
                        encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
                        namespace="urn:examples:helloservice"
                        use="encoded"/>
                </input>
                <output>
                    <soap:body
                            encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
                            namespace="urn:examples:helloservice"
                            use="encoded"/>
                </output>
            </operation>
        </binding>
        <service name="Hello_Service">
            <documentation>WSDL File for HelloService</documentation>
            <port binding="tns:Hello_Binding" name="Hello_Port">
                <soap:address
                        location="http://localhost:8080/soap/rpcrouter"/>
            </port>
        </service>
    </definitions>
    ```
    - `<service>`: HelloService.
    - `<types>`: Использование импортированной по локальному адресу XML Schema.
    - `<message>`: "sayHelloRequest": "firstName" параметр, "sayHelloResponse": "greeting" возвращаемое 
    значение
    - `<portType>`: sayHello операция, которая состоит из request-response сервиса.
    - `<binding>`: Указание использовать SOAP HTTP протокол.
    - `<service>`: сервис доступен по ссылке http://www.examples.com/SayHello/.
    - `<port>`: Связывает `<binding>` с URI http://www.examples.com/SayHello/, по которой доступен данный сервис.

***

### 5. UDDI

1. **UDDI (Universal Description, Discovery, and Integration)** - предоставляет всемирный реестр веб сервисов для рекламы, поиска и хранения. <sup>[\[5\]][uddi]</sup>
   - UDDI предоставляет структуру для представления деловых отношений, веб сервисов, технических метаданных и точек доступа к веб сервисам.

***

### 6. REST

1. **REST (REpresentational State Transfer)** - это стиль архитектуры программного обеспечения для распределенных систем, использующий веб протоколы и веб технологии. REST архитектура включает в себя клиентское и серверное взаимодействие, построенное вокруг передачи ресурсов. <sup>[\[6\]][rest]</sup>
   - Самая большая реализация REST - World Wide Web, которая, как правило, используется для построения веб-служб.
   - Системы, которые построены согласно REST принципам, называются RESTful.
   - REST может быть использован для сбора данных вебсайта через XML файлы веб страницы.
   - Пользователи могут обращаться к веб страницам через URL сайта, взаимодействовать с XML файлами через браузер и использовать данные как угодно.
   - Базовые REST принципы:
      + Client и Server - клиент и сервер должны быть отделены от REST операций через специальный интерфейс, который улучшает переносимость кода.
      + Stateless - каждый клиентский запрос должен содержать все требуемые данные для обработки запроса без хранения клиентского окружения на сервере.
      + Cacheable - ответы могут быть закэшированны на клиентском компьютере, чтобы ускорить веб поиск.
      + Layered System - позволяет клиентам подключаться к серверу через вспомогательный уровень для улучшения расширяемости.

2. Клиент/сервер связь:
   ```
                     HTTP GET, POST, PUT, or DELETE
     REST: client ----------------------------------> service

           client <---------------------------------- service
                    XML, JSON, plaintext,... document
   ```

***
      
### 7. Protocol Stack

1. **Протокол** -  набор соглашений интерфейса логического уровня, которые определяют обмен данными между различными программами.

2. **TCP/IP** - семейство протоколов, предназначенных для взаимодйествия между электронными устройствами. Определяет, как они должны быть связаны через интернет и как нужно передавать данные между ними. <sup>[\[7\]][tcp/ip]</sup>

3. **TCP (Transmission Control Protocol)** - отвечает за разбиение данных на небольшие пакеты перед тем, как пересылать их по сети, и за сборку этих пакетов в исходное состояние после получения. <sup>[\[7\]][tcp/ip]</sup>

4. **IP (Internet Protocol)** - отвечает за обмен данными между устройствами, т.е. за адресацию, отправку и получение пакетов данных через интернет. <sup>[\[7\]][tcp/ip]</sup>

5. **DNS (Domain Name Server)** - иерархическая система имен, построенная на распределенных базах данных. <sup>[\[7\]][dns]</sup>
	- Когда пользователь посещает сайт, то имя сайта преобразуется в числовое представление с помощью DNS.
	- Когда регистрируется новый домен вместе с TCP/IP адресом, DNSs по всему миру фиксируют эту информацию.

1. **HTTP (HyperText Transfer Protocol)** - протокол уровня приложения, используемый в основном в World Wide Web. HTTP использует клиент-серверную модель, где браузер является клиентом и общается с веб-сервером, который хостит веб-сайт. <sup>[\[7\]][http]</sup>
	- Обычный HTTP запрос состоит из следующих шагов:
		+ Открывается соединение к HTTP серверу.
		+ Запрос отправляется на сервер.
		+ Выполняются вычисления на сервере.
		+ Сервер посылает назад ответ.
		+ Соединение закрывается.
	- Для HTTP, действие над данными задается с помощью методов (CRUD операций):
		+ GET - получить.
		+ PUT - добавить, заменить.
		+ POST - добавить, изменить, удалить.
		+ DELETE - удалить.

2. **HTTPS (HyperText Transfer Protocol Secure)** - разновидность HTTP протокола, который добавляет передаваемым данным уровень безопасности через SSL протокол или TLS протокол.

3. **FTP (File Transfer Protocol)** - протокол, используемый для передачи или обмена файлами между компьютерами.
4. **IIOP (Inter-ORB Protocol)**
3. **SSL (Secure Socket Layer)** - стандартный протокол, используемый для защищенной передачи документов через сеть.
4. **TLS (Transport Layer Security)** - улучшенная версия SSL протокола.
5. **SNMP (Simple Network Management Protocol)** - используется для управления сетями.
6. **RARP (Reverse Address Resolution Protocol)**
6. **PPTP (Point to Point Tunneling Protocol)**
6. **NTP (Network Time Protocol)**
6. **LDAP (Lightweight Directory Access Protocol)**
6. **ICMP (Internet Control Message Protocol)**
6. **DHCP (Dynamic Host Configuration Protocol)**
6. **BOOTP (Boot Protocol)**
6. **ARP (Address Resolution Protocol)**
6. **IMAP (Internet Message Access Protocol)**
6. **POP (Post Office Protocol)**
6. **MIME (Multi-purpose Internet Mail Extensions)**
6. **SMTP (Simple Mail Transfer Protocol)**

***

### 8. Технологии

1. **Servlet API** является основой для всех остальных технологий Java, касающихся Web и дает возможность динамически генерировать любой web-контент, используя любые библиотеки, доступные для java. 

1. **JSP (JavaServer Pages)** - технология, используемая для разработки интерактивных веб страниц. JSP была разработана Sun Microsystems и является улучшенной версией Java сервлетов. <sup>[\[8\]][jsp]</sup>
  - Как и большинство серверных технологий, JSP отделяет бизнес логику от представления.
  - JSP являются обычные HTML страницы с встроенным Java кодом.
  - Чтобы обработать JSP файл, разработчику нужен JSP движок, который подключен к веб серверу. 
  - JSP страница компилируется в сервлет, который управляет сервлет движком (этот этап называется "преобразованием"). Сервлет движок затем загружает класс сервлета и реализовывает его, чтобы создать динамический HTML, который затем посылается в браузер. Такой процесс запускается каждый раз, когда запрашивается очередная страница.
  - Если вместе с JSP исользовать JDBC, то можно сделать динамические, связанные с базой данных, вебсайты.

1. **Apache Tomcat** - опенсорсный веб сервер, разработанный Apache Software Foundation. Он позволяет реализовывать Java сервлеты и JSPs для поддержки эффективных Java-серверных сред. <sup>[\[8\]][tomcat]</sup>
  - Пользователь также может получить доступ к конфигурациям и использовать XML для настройки проектов.
  - Tomcat может предоставить рантайм оболочку для Java сервлетов.
  - Ключевой элемент Java-based веб сервера - сервлет контейнер, поэтому JSP скрипты и им подобные автоматически преобразовываются в сервлет.
  - **Catalina** — контейнер сервлетов Tomcat’а, который реализует спецификацию сервлетов.

1. **Apache Ant** - Java-based опенсорсный build tool, разработанный Apache Software Foundation. Он схож с "make" утилитой, но в большинстве своем функционирует только на java платформе. <sup>[\[8\]][ant]</sup>
   - В отличии от Make, Ant написан на XML, поэтому портируемость и простота - это два главных преимущества Ant.

1. **RPC (Remote Procedure Call)** - класс технологий, позволяющих компьютерным программам вызывать функции или процедуры в другом адресном пространстве (как правильно, на удаленных компьютерах). <sup>[\[8\]][rpc]</sup>
  - RPC работает по принципу: отправитель или клиент создает запрос с помощью процедуры, функции или вызова метода в удаленный сервер, который RPC обрабатывает и посылает. Когда удаленный сервер получает запрос, он отсылает ответ назад клиенту, и приложение продолжает свою работу. Перед тем, как продолжать работу программы, клиент ждет, пока сервер завершит процесс обработки.
  - В общем, RPC приложения используют модули, называемые прокси и заглушки, которые заставляют их выглядеть как простые локальные вызовы процедур.
	- RPC-ориентированное приложение - приложение, в которых существует интерактивная связь между удалёнными компонентами с небольшим временем ответов и относительно малым количеством передаваемых данных.

1. **RMI (Remote Method Invocation)** - программный интерфейс вызова удаленных методов в языке Java. <sup>[\[8\]][rmi]</sup>
	- Он представляет объектно-ориентированный эквивалент RPC.
	- RMI функциональность находится в `java.rmi` пакете и предоставляет распределенную объектную модель, специфицирующую, каким образом производится вызов удаленных методов, работающих на другой виртуальной машине Java.
	- При доступе к объектам на другом компьютере возможно вызывать методы этого объекта. Необходимо только передать параметры метода на другой компьютер, сообщить объекту о необходимости выполнения метода, а затем получить обратно возвращаемое значение. 
1. **RSS (Really Simple Syndication)**

2. **RDF (Resource Description Framework)**
	
***

[rpc]: https://www.techopedia.com/definition/24022/remote-procedure-call-rpc
[wsdl]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=12&zoom=auto,-83,820
[uddi]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=12&zoom=auto,-83,820
[soap]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=12&zoom=auto,-83,820
[jsp]: https://www.techopedia.com/definition/4886/javaserver-page-jsp
[rest]: https://www.techopedia.com/definition/1312/representational-state-transfer-rest
[tomcat]: https://www.techopedia.com/definition/15735/apache-tomcat
[rest]: https://www.techopedia.com/definition/1312/representational-state-transfer-rest
[ant]: https://www.techopedia.com/definition/16219/apache-ant
[tcp/ip]: http://www.w3schools.com/website/web_tcpip.asp
[http]: https://www.techopedia.com/definition/2336/hypertext-transfer-protocol-http
[https]: https://www.techopedia.com/definition/5361/hypertext-transport-protocol-secure-https
[dns]: https://www.techopedia.com/definition/5361/hypertext-transport-protocol-secure-https
[rmi]: https://www.techopedia.com/definition/1311/remote-method-invocation-rmi

[1.4]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=22&zoom=auto,-83,751
[1.5]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=22&zoom=auto,-83,751
[1.6]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=18&zoom=auto,-83,662
[1.7]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=23&zoom=auto,-83,400
[1.8]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=24&zoom=auto,-83,471
[1.9]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=24&zoom=auto,-83,828

[2.diagram]: http://gsl.mit.edu/media/programs/south-africa-summer-2015/materials/o'reilly_-_java_web_services.pdf#page=12&zoom=auto,-83,10

