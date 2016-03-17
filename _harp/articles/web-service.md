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
 
4. Пример веб сервиса: [dailyinfo](http://www.cbr.ru/dailyinfowebserv/dailyinfo.asmx) 

### 2. Основные компоненты

1. **SOAP (Simple Object Access Protocol)** - основанный на XML язык, описывающий веб сервисы.

2. **REST (REpresentational State Transfer)** - стиль архитектуры веб сервиса.

3. **WSDL (Web Services Description Language)** - язык программирования, основанный на XML, преднзначенный для 
описания веб сервисов.

4. **RDF (Resource Description Framework)** - фреймворк, написанный на XML, предназначенный для описания ресурсов в 
сети.

5. **RSS (Really Simple Syndication)** - семейство XML форматов, предназначенных для публикации обновленной 
информации, такой как: лента новостей, записи в блогах, аудио и видео материалы.

### 3. SOAP

1. Пример взаимодействия клиента с Web приложением (регистрация аккаунта):
   ```
   1. Программа на клиентской стороне конвертирует информацию о регистрации аккаунта в SOAP сообщение.
   2. SOAP сообщение отсылается в веб сервис, как тело HTTP POST запроса.
   3. Веб сервис распаковывает SOAP реквест и конвертирует в комманду, которую понимает приложение на сервере.
   4. Приложение обрабатывает информацию своей логикой и отправляет ответ с новым уникальным номером аккаунта.
   5. Следующим шагом, веб сервис конвертирует ответ сервера в SOAP сообщение, которое отправляет назад в клиентское 
   приложение, как ответ на HTTP запрос.
   6. Клиентское приложение распаковывает SOAP сообщение и предоставляет клиенту соотвествующую информацию.
   ```
   
### 4. XML WSDL

1. **WSDL Documents** - WSDL документ описывает веб сервис. Он указывает местоположение сервиса и его методы, 
используя следующие элементы:
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
    