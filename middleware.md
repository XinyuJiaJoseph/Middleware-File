# Week1-part1

# Middleware

## 1.Middleware

(1) concept: Middle is a software or hardware that allows two
or more heterogeneous computing components to communicate and interact.

Application layer->Middle Layer->Platform Layer

(2) types:

– Object-Oriented Middleware (OOM)
	• Remote Method Invocation (RMI)
	• Remote Procedure Call (RPC)
	• Object Request Broker (ORB)
– Transaction Processing Monitor (TPM)
– Reflective Middleware (RM)
– Message-Oriented Middleware (MOM)

(3) function:

- Enterprise systems communicate

- Software written in different languages run and communicate

- Users may want to access or transfer data from different systems to different platforms

  Win->Linux: WinSCP, Putty		Linux->Win: Remote Desktop protocol

## 2. Messaging

(1) concept: a method of communication between software components or applications

- peer-to-peer/enable distributed communication/Sx&Rx do not need to know anything
- differ from electronic mail
- is used for communication between software applications or software
  components

(2) Advantage:

- Heterogeneous Integration 异构集成
- Reduce System Bottlenecks 减少系统瓶颈
- Increase Scalability 提高可扩展性

## 3. Messaging Service

concept: a software component functionality based on service-oriented architecture which allows users to create, send, receive, read, delete and save messages in form of texts, audio, pictures and video from one software component to another and vice versa.

Types of Messaging Services

- Cloud Messaging Service
- Short Message Service (SMS)
- Instant Message Service (IMS)
- Multimedia Message Service (MMS)



# Message-oriented Middleware

(1) Concept: **a software or hardware that provides a communication channel** between heterogeneous applications platforms and systems by passing messages across between the communicating systems.

(2) function:

- provides capabilities for sending and receiving messages among distributed systems
- uses the extensible Messaging and Presence Protocol (XMPP) for communication
- provides asynchronous message-based communicationbetween modules and processes

## Architecture

![image-20201214160442141](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214160442141.png)



### MOM Client - Producer

- is used by the client to produce a message
- The message is then sent by the message producer
- The message is usually sent to a physical destination which is written in the API using the destination object

### Message Broker 消息代理

functions:

- is responsible for receiving and sending the message
- facilitates the connections between producers, administration services and consumers
- maintains a persistent data store to reliably send data
- provides secure connection using encrypted SSL authenticated connection.

### MOM Client - Consumer

- the message is automatically given to “Message Listener” object that is defined by the consumer
- messages can be consumed by only the messages that match the properties selected by a consumer

### Types of MOM

- Message Queuing
- Publish / Subscribe



## MOM Messaging Models

### Point-to-Point

- **one sender sends a message to only one receiver at a time**
- It is a **one-to-one** relationship
- Messages are sent to the particular address specified by the client

### Publish/Subscribe

- **one sender sends one message that is received by many receivers or many messages are sent and are received by many receives**
- **a one-to-many or many-to-many relationships**
- The sender and receiver of messages are decoupled
- There is no need for the producer and consumers to be running at the same time



## Advantage of MOM

- Hides the complexity of applications running on different operating systems
- The mode of sending and receiving messages is reliable
- MOM embeds security features so that messages cannot be intercepted and changed
- It sends messages asynchronously and so the receiver does not have to know that messages are being sent prior to sending them
- Allows heterogeneous systems to communicate
- Allows different programming languages to be ported(portability) across different platforms

## Types of Pub-Sub message

- Topic-Based

  uses a hierarchical naming scheme

  drawback: too restrictive as it uses specific terms

- Content-Based

  uses commonly used query-like syntax for subscription of contents

  advantage: less restrictive as it does not use specific terms for subscriptions

- Type-Based

  The messages are represented as objects

  disadvantage: restrictive as subscribers need to register for the type of messages they want to subscribe

## Pub/Sub Model

![image-20201214161932234](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214161932234.png)

## Types of Queuing Systems in MOM

- FIFO
  - The first message sent will be the first to be received and the last will be the last to be received
- FIFO with Priorities
  - It is the same as FIFO but the message sent/received depends on the priority set for the publisher and consumer
- Journal Queue
  - The system keeps track and copy of all messages
- Public Queue
  - It is open for access to all users
- Private Queue
  - It requires authentication and authorization to use the queue
- Connector / Bridge
  - This is a proxy to connect to commercial MOM’s queues

# Java Message Service

## Concept

- is a Java Application Programming Interface (API) that **allows applications to create, send, receive and read messages**
- minimises the set of concepts programmers need to learn to use messaging products
- enables loosely coupled communication as well as Asynchronous communication
- **is reliable as it ensures that a message is delivered once and only once**

## When to use JMS API

- The enterprise application provider wants the components not to depend on information about components’ interfaces, so that components can be **easily replaced (loose coupling)**
- The provider wants the application to run whether or not all components are up and running simultaneously (asynchronous communication)

## JMS API Architecture

![image-20201214162732074](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214162732074.png)



### JMS Provider

- This is the messaging system which implements the JMS interfaces and provides administrative and control functionalities

### JMS Clients

- These are Java programs or components that produce and consume messages

### Messages

- These are the objects that communicate information between JMS Clients

### Administered Objects

- Preconfigured JMS objects created by an administrator for the use of clients
- types: Destinations (D) and Connection Factories (CN)

### JNDI Namespace

- This is a Java directory service API that allows Java program clients to discover and look up data and objects through a name.
- connects a java application to external directory services

## JMS Messaging Domains

- Messaging Domain
  - Messaging domain is the concept of how message is published and consumed with regards to the systems used by the provider and clients.
- Types of Java Messaging Domains
  - **Point-to-point (PTP) messaging domain**
    - based on the message queues, senders and receivers concept
    - ![image-20201214164047898](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214164047898.png)
  - **Publish/Subscribe messaging domain**
    - allows clients to address messages to a topic that functions similar to a bulletin board
    - ![image-20201214164200094](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214164200094.png)

## Types of JMS Message Consumption

- Synchronously
- Asynchronously

## JMS Programming Model

two parts of JMS app: Destination/connection factories

![image-20201214164302584](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214164302584.png)

### Connection Factory

- the object a client uses to **create a connection with a provider**

- encapsulates a set of connection configuration parameters has been defined an administrator

- an instance of either the **QueueConnectionFactory** or the **TopicConnectionFactory** interface

  ![image-20201214164813082](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214164813082.png)

### Connections

- A connection encapsulates a virtual connection with a JMS provider
- representation an open TCP/IP socket between a client and a provider service daemon(守护程序)

### Destinations 

- A destination is the object a client uses **to specify the target of messages it produces and the source of message it consumes**

### Sessions

- A session is **a single threaded context for producing and consuming messages**
- use sessions **to create message producers, message consumers and messages**

### Message Producers

- A message producer is **an object created by a session and is used for sending messages to a destination**

### Message Consumers

- A message consumer is an object created by a session and is used for receiving messages sent to a destination
- Use the receive method for both TPT and Pub/Sub to consume messages synchronously.

### Message Listeners

- A message listener is an object that acts as an asynchronous **event handler** for messages
- *onMessage* method

### Message Selectors

- If your messaging application needs to filter the message it receives
- allows a message consumer to specify the messages it is interested in

### Message

- Message Header(needed)
  - contains a number of predefined fields that contain values that both clients and producers use to identify and route messages
  - has a unique identifier represented by the header field JMSMessageID
- Message Properties(optional)
  - Consists of some information in the header
  - The properties are used to extend the functionality of the header
  - Programmers can create properties to describe the message they want to send or receive
- Message Bodies(optional)
  - The body contents the message and how it will be sent and received

### Example

- Context -> Topic / Queue
- Connection Factory -> Connection -> session -> sender / receiver / publisher / subscriber

```java
//Connection Factories
Context ctx = new InitialContext();

QueueConnectionFactory queueConnectionFactory = (QueueConnectionFactory)ctx.lookup("QueueConnectionFactory");

TopicConnectionFactory topicConnectionFactory = (TopicConnectionFactory)ctx.lookup(“TopicConnectionFactory”);

//Connections
QueueConnection queueConnection = queueConnectionFactory.createQueueConnection();

TopicConnection topicConnection = topicConnectionFactory.createTopicConnection();

//Destinations
Topic myTopic = (Topic) ctx.lookup(“MyTopic”);
Queue myQueue = (Queue) ctx.lookup(“MyQueue”);

//Sessions
TopicSession topicSession = topicConnection.createTopicSession(false,Session.AUTO_ACKNOWLEDGE);

//Message Producers
QueueSender queueSender = queueSession.createSender(myQueue);
TopicPublisher topicPublisher = queueSession.createPublisher(myTopic);

queueSender.send(message);
topicPublisher.publish(message);

//Message Consumers
QueueReceiver queueReceiver = queueSession.createReceiver(myQueue);
TopicSubscriber TopicSubscriber = topicSession.createSubscriber(myTopic);

//Message Consumers' start method
queueConnection.start();
Message m = queueReceiver.receive();
topicConnection.start(0);

//Message Listeners
TopicListener topicListener = new TopicListener();
topicSubscriber.setMessageListener(topicListener);
```

------



# Week1-part2

# Java Server Pages

- JSP is used to implement the “View” part of MVC design pattern
- usually deployed using **Apache Tomcat Servlet** Container and Web server
- Java Servelets are Java classes used to replicate or extend the capabilities of the web server deployed with JSP

### Architecture of JSP

![image-20201214193547296](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214193547296.png)



## Web

### web server

#### functions: receive/look for/send back

- **The web server receives the request from clients**
- The web server **looks for the resource that the client has requested for**
- finds the resource and **sends back results** of the request to clients

### Client(客户端)

- The web client (**Browser**) allows the user **to request for resources from the web server**
- **displays the results of the resource** obtained from the web server to the user

### Tomcat

![image-20201214193822420](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201214193822420.png)

## Servlet

#### Controller

- They take clients request and give back to clients response
- use the **HttpServletRequest and HttpServletResponse** objects for serving clients
- Servlets are managed by the Container

### Java and Javabeans

- Model
- are used to implement the business logic (actions) for the web application

### Web Container–Apache Tomcat

- Servlets are deployed in a container—because Servlets do not have the “main()” method that initiates the running of the application

#### Functions

- Support for JSP-translates JSP codes to Java codes
- Life-cycle management
- Security
- Communication
- Multi-threaded support

## JSP Implementation

- Java codes implemented within HTML is known as JSP
- <% *code* %>

### JSP Directives

page directive: (dynamic动态的 at run time)

- <%@ page import = "java.util.*" %>

include directive: (static静态的)

- <%@ include file = "hello.jsp" %>

taglib directive

- <%@ taglib tagdir=“/WEB-INF/tags/foo” prefix=“foo” %>

attribute directive

- <%@ attribute name=“<text>” required=“[Boolean]” 

  rtexprvalue=“[Boolean]” %>

### JSP Expression

- <%= new Date() %>
- is converted to out.print(new Date());

### JSP Scriptlet

use sciptlet -> use <% %>

### JSP Declaration

```jsp
<%! Date myDate = new Date();
Date getDate() {
	System.out.println( "getDate() method" );
	return myDate;
}
%>
```



### JSP Actions

types: 

- Standard actions:	<jsp:tag />

- custom actions:    <c:tag />



### JSP Expression Language (EL)

- EL always start with a $ followed by an open curly brace and the followed by an object or an attribute and then finally closed by a closing curly brace.
- ${person["name"]} / ${person.name}    两个输出相同
  - dot”.” -> ${first.second} -> {*map/bean*.**map key/bean property**}
  - brackets”[]” -> ${first[“second”]} -> works for arrays and list objects
- EL handles “null” values by not printing them at all
- 可能throw error
- 无效值为0，可能出现infinity



### JSP and Bean

e.g. standard actions of JSP and Bean

```jsp
<jsp:useBean id=“<text>” class=“<class>” scope=“<scope>”/>

<jsp:useBean id=“student” class=“department.Student” scope=“session” />

```

get property of a Bean

```<jsp:getProperty name=“student” property=“name” />```

set property of a Bean

```jsp
<jsp:useBean id=“student” class=“department.Student” scope=“session”
	<jsp:setProperty name=“student” property=“Grade” value=“90%” />
</jsp:useBean>
```

### Looping

<c:forEach var=“bookTitle” items=“${bookShelf}” >
${book}
\</c:forEach\>

### Conditional Statements

<c:if test=“${studentNo le 2000} “ >
	<jsp:include page =“student_bupt.jsp” />
\</c:if\>

\<c:choose>/ \<c:when\> / \<c:otherwise\>

### Lifecycle of a JSP

![image-20201215002238967](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215002238967.png)



![image-20201215002252505](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215002252505.png)



------



# Week1-part3

# Servlets

- **concept**: Are programs that run on web server acting as middle layer between **HTTP request** and **databases or other applications**.

- Used to generate dynamic web pages in response to client.

  ![image-20201215002649473](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215002649473.png)

- the context of servlets: the business logic/the presentation logic

#### The pro of dynamic pages:

- The web page is based on data submitted by the user, or
- The web page is derived from data that changes frequently
- The web page uses information from corporate databases or other server-side sources

#### The pro of servlets over CGI: 

efficient, convenient, powerful, portable, secure, inexpensive

## What servlets do

- Read any data sent by the user
- Look up info embedded in HTTP request
- generate results/format results inside a document
- Set appropriate HTTP response parameters
- Send the document back to the client

e.g. tomcat is a web server

![image-20201215003642769](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215003642769.png)

![image-20201215003749105](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215003749105.png)



## Calling servlet

- executing a method of a servlet class instance, not looking at a page

- servlet handle processing: handing/calculation/database queries

  JSP is used to format the results

## Container (Servlet is deployed in)

- a program that receives requests to servlets from a web server application
- manages the life cycle of its servlets

#### init() from GenericServlet

not override:

```public void init(ServletConfig config) throws ServletException;```

usually override:

```public void init() throws ServletException;```



## Deployment Descriptor (DD)

- Map servlet name with servlet class and URL pattern



### Servlet Lifecycle Methods

- init()
  - Only once 
  - must complete before the service() is called
- service()
  - once or several times to call the servlet methods
- destroy()
  - once for garbage collection
  - When the service method has finished

## Servlet Life Cycle

![image-20201215004931601](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215004931601.png)



#### Handle the client request: HTML form data

- form data is used to transfer information via POST or GET
- Servlets have built-in features to parse this data

### ServletConfig objects

- ServletConfig
  - Each servlet has one ServletConfig
  - contains parameter’s from the server’s configuration file
  - Each servlet uses it to define deployment time information and parameters without hard coding them
  - It is used to access ServletContext
- ServletContext
  - This is defined once for a whole single application
  - This is used to define web application parameters
  - It is configured in the DD and contains initialization parameters for the web application

#### e.g.

- DD中有某个参数

```
// method 1
ServletContext ctx = getServletContext();
ctx.getParameter();
// method 2
out.println(getServletConfig().getInitParameter(“lecturersEmail”)
// method 3
public void init() throws ServletException {
	String initPath = getServletConfig().getInitParameter(“count_file”);
	System.out.println(initPath);
}
```



### Output Objects

- PrintWriter
  - This is used to print text to a character stream
- OutputStream
  - This can print any output, text, html, bytes, etc

##  Example

```java
import javax.servlet.http.*;
import javax.servlet.*;
public class AnyHttpServlet extends HttpServlet {
public void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    
};
public void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    
};
}
```



# Week1-part4

# Java Spring

![image-20201215133823352](C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201215133823352.png)

## Functions

- Supports all major application servers and JEE standards.
- Handles the infrastructure so you can focus on your application.

## Core container

- The Core module provides the fundamental parts of the framework, including the IoC and Dependency Injection features.
- **The Bean module** provides BeanFactory, which is a sophisticated implementation of the factory pattern.
- **The Context module** builds on the solid base provided by the Core and Beans modules and it is a medium to access any objects defined and configured. The ApplicationContext interface is the focal point of the Context module.
- **The SpEL module** provides a powerful expression language for querying and manipulating an object graph at runtime

## Data Access / Integration

- **The JDBC module** provides a JDBC-abstraction layer that removes the need for tedious JDBC related coding.
- Modules: ORM, OXM, Transaction

## Web

- **The Web module** provides basic web-oriented integration features such as multipart file-upload functionality and the initialization of the IoC container using servlet listeners and a web-oriented application context.
- Modules: Web-MVC, Web-Socket, Web-Portlet

## Why Spring

- A popular and stable **Java application framework** for enterprise
  development
- A primary purpose is to reduce dependencies and even introduce **negative dependencies**

#### Problem of traditional approach

hard to test/reuse/understand/maintain(one bug connect with more)

## Dependency Injection(define Spring)

- An **injection** is the **passing of a dependency** (a service) to a **dependent object** (a client).
- Dependency Injection helps to keep our classes as independent as possible.
- Increase reuse by applying **low coupling**
- two forms: Setter Injection and Constructor Injection

## Inversion of Control

- Inversion of Control is a principle in software engineering by which the control of objects or portions of a program is transferred **to a container or framework**.
- If we want to add our own behavior, we need to extend the classes of the framework or plugin our own classes

### Components of Spring IoC

- **Spring IoC Container** is the platform

- Bean factory produce beans

- Configuration file defines beans and the main flow

- is represented by interface *ApplicationContext*

  for standalone applications: *ClassPathXmlApplicationContext and*

  *FileSystemXmlApplicationContext* 

  for web applications: *WebApplicationContext*

## Bean

- with a unique id
- Two types
  - Singleton — created and referenced each time it is requested
  - Prototype — new bean created each time
- key attributes: class/id/configuration/constructor/property/Collaborators

### Bean Factory

- seen as an ApplicationContext
- Spring uses a BeanFactory to create, manage and locate “beans” which are basically instances of a class
- Beans are created using constructors (mostly no-arg) or factory methods

### How are beans injected?

- A dependency graph is constructed based on the various bean definitions
- Beans are created using constructors (mostly no-arg) or factory methods
- Dependencies that were not injected via constructor are then injected using setters
- Any dependency that has not been created is created as needed

### Multiple bean config files

three ways to load:

- Load multiple config files from web.xml
- Use the import tag
- Load multiple config files using Resources in the application context constructor

## Examples

```
<bean id="exampleBean" class="org.example.ExampleBean">
	<property name="beanOne"><ref bean="anotherExampleBean"/></property>
	<property name="beanTwo"><ref bean="yetAnotherBean"/></property>
	<property name="integerProperty"><value>1</value></property
</bean>

public class ExampleBean {
	private AnotherBean beanOne;
	private YetAnotherBean beanTwo;
	private int i;
	public void setBeanOne(AnotherBean beanOne) {
		this.beanOne = beanOne; 
	}
	public void setBeanTwo(YetAnotherBean beanTwo) {
		this.beanTwo = beanTwo; 
	}
	public void setIntegerProperty(int i) {
		this.i = i; 
	}
}
```

# Aspect Oriented Programming

- AOP entails breaking down program logic into distinct parts called concerns.

## Terminology

- Aspect - Set of API for cross-cutting
- Join point - A method invocation
- Advice - Action to take at a join point
- Point cut - A set of join points
- Target - Object containing the join point

## Types of Advices

- before
- after
  - after returning
  - after throwing
  - around
    - Run advice before and after the advised method is invoked

## Examples

```java
public class TrackOperation { // Aspect class
    @Pointcut("execution(* Operation.*(..))")
        public void k(){}//pointcut name
    @Before("k()")//applying pointcut on before advice
    public void myadvice(JoinPoint jp)//it is advice (beforeadvice)
    {
        System.out.println("additional concern");
    }
}

public class Operation {
	public void msg(){ System.out.println("msg method invoked");}
	public int m(){
        System.out.println("m method invoked"); 
        return 2;
    }
	public int k(){
        System.out.println("k method invoked");
		return 3;
    }
}
```



# Week2-part1

# Concurrency

### Concept:

**Process**: This is an instance of a computer program that is executed and is running

Thread: This is the smallest part of a program instruction that runs and is managed independently by a scheduler of an operating system or a Java Virtual Machine(JVM) in case of Java programs

## Life Cycle of a Thread

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201217014205999.png" alt="image-20201217014205999" style="zoom:67%;" />

- New
  - This is when the Thread instance is created using the “new Thread()” command. The thread is still not alive yet
- Runnable
  -  This is when the Thread instance variable invokes the “start()” method using the “t.start()” command, where t is the thread instance variable. The  thread is now alive and **has joined the queue of threads about to be executed**
- Running
  - This is when the Thread is now executing
- Blocked / Waiting /Sleeping
  - This is when the Thread goes out of the execution or running mode when the wait, interrupt or sleep commands are executed
- Dead
  - This is when the Thread completes its task terminates execution calling “t.destroy()” command for garbage collection.

#### JVM is a process

A Java application runs by default in one process

Java Virtual Machine (JVM)

### Process and threads

- The resources of the process are allocated to it via the operating system
- Each thread has its own **call stack** but can access shared data of other threads in the same process
- Every thread has its own **memory cache**

## Three concepts 

- Atomicity
  - An operation is said atomic when it cannot be interrupted.
- Visibility
  - This occurs when a thread must watch the actions of another thread
  - e.g. for the termination of the thread
- Order of execution
  - The order of execution is not guaranteed



### The Thread class

the Thread class manages the running of the thread

Two ways of giving the Thread the run method:

- Passing a runnable object to the Thread constructor
- Creating an instance of a new class that inherits the Thread class, explicitly specifying the run method in the class

## Example

- Method1

```java
//Declare a Runnable
public class MyFirstRunnable implements Runnable {
	//runnable is an interface requires to implement run()
    public void run() {
        // in a thread
    }
}

public class MyFirstTest {
    public static void main () {
        //Create the new Thread instance and start
        Thread thread = new Thread(new MyFirstRunnable());
        thread.start();
    }
}
```

```java
Thread t = new Thread(new Runnable() {
	public void run() {
	
	}
});
t.start();
```

- Method 2

```java
public class MyThread extends Thread {
	public void run() {
        
    }
    MyThread myThread = new MyThread();
    myThread.start();
}
```

#### The default run method of the class Thread:

`public void run(){	if(target!=null)		target.run();	}`

#### Thread sleep

Thread.sleep(1000);



## Interrupt

- An interrupt is an indication to a thread that it should stop what it is doing and do something else.
- **It doesn’t stop the thread**
- *t.interrupt()*
- **The interrupted thread must support its own interruption**
- if the thread is **sleeping** or **joining** or **waiting** on another Thread
  -  an InterruptedException is thrown.
  -  and then the interrupted status of the Thread will be cleared
- 用try catch 来 catch InterruptedException

### Join

- Waiting for another thread to die/sleep

- *t.join();*

- ```java
  try{
  	thread2.join();	//wait for thread2 die
  } catch(InterruptedException e){
  	e.printStackTrace();
  }
  ```

  

### Block

- **A thread that is prevented from executing is said to be blocked.**
- Reason:
  - It has been put to sleep for a set amount of time
  - It is suspended with a call to suspend()and will be blocked until a resume() message
  - The thread is suspended by call to wait(), and will become runnable on a notify or notifyAll message.

### 不同状态

#### **interrupted status is initially false**

when a thread is interrupted by some other thread through a call to Thread.interrupt(), one of two things happens:

- If that thread is executing a low-level interruptible blocking method, it unblocks,resets and throws InterruptedException
- Otherwise, interrupt() merely sets the thread interruption status.

### 一个处于interrupt状态的thread

flag: the interrupted status

- can be read with Thread.isInterrupted()
  - query **other's** interrupt status
  - instance method
  - **only looking**
  - *myThread.isInterrupted()*
- can be read and cleared in a single operation with **Thread.interrupted()**
  - **static** 只能 *Thread.interrupted()*
  - Only chech the current thread
  - and the interrupt status is cleared

错误：if (myThread.interrupted()) {    }

正确：if (myThread.isInterrupted()) {}

## Terminate a Thread (3 ways) 终止

- The thread has finished the work it is designed to do, and exits the run()method naturally.

- The thread has received an interruption signal, while doing its work.
  
  - It decides to not continue with work and exits the run() method.
  
- The thread has been marked as **daemon thread守护线程**. When the parent thread who created this thread terminates, this thread will be forcefully terminated by the JVM.

  非守护线程结束时，程序终止并杀死所有守护进程



### Override

- take advantage of the compiler checking to make sure you actually are overriding a method when you think you are
- can use it to mark when a method implements an interface for the same benefits.

## 线程安全

- interrupt again as may need to do something rather than just exit
- nterruptedException does not make your thread “interrupt safe”
- 因为catch以后，线程状态不interrupt了，需要在catch block 里 *Thread.currentThread().interrupt()*
- 可添加continue;

## Deamon

- setDaemon(false)
  - **the Worker thread continues to run** after main has finished.
- setDaemon(true)
  - work thread terminates when the main thread terminates



# Week2-part2

# Java Memory Model

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201217095322204.png" alt="image-20201217095322204" style="zoom:67%;" />

## Stack

- Not visible to other threads.
- primitive types as local variables
- may pass a copy of a primitive variable to another thread
- **local variable in** **object methods are on the stack**

e.g. 两个thread使用同一个object的method，他们需要进入object的成员变量，但是他们都有各自的本地变量的备份

## Heap

- the object itself if stored on the heap
- **Static class variables are also stored on the heap**

#### The architecture

main memory speed < **CPU cache memory speed** < CPU internal register speed

when CPU need to access M.m it will read part of M.m into its CPU cache

## Some problems

#### when storage in dif memory areas

### Visibility

- Visibility of thread updates (writes) to shared variables.
- As long as the CPU cache has not been flushed back to main memory, the changed version of the shared object is not visible to threads running on other CPUs.
- each copy sitting in adifferent CPU cache

### Race conditions

- A, B 读同一个the variable count of a shared object into its CPU cache，(B into a different CPU cache) A改了，B也改了，A，B写回to main memory，不知道对方的修改
- The variable has been incremented two times, once in each CPU cache.

### Volatile易变的

- a variable value is modified by dif threads

- **The value of this variable will never be cached thread-locally**: all reads and writes will go straight to "main memory";

- +=  不安全

- when not to use: 

  not necessary for fields  that are immutable

  not suitable for complex operations when need to prevent access

- when to use:

  the value to write doesn’t depend on the current value

### Thread.yield()

- yield stops the thread running continuously and gives some time back to the OS.
- It just gives up the thread's turn, and regains it in the next round.

### Thread.interrupt()

**advantage**: is that you can immediately break out of interruptable calls, which you can't do with the flag approach.

### 如果一个thread在正常运行状态，interrupt不会throw exception

## Critical sections临界区

- The code segments within a program that access the same data from within separate, concurrent threads are known as critical sections

  e.g. Thread 1: Read the value, get 0, add 1, so value = 1
  	   Thread 2: Read the value, get 0, add 1, so value = 1

- 用 *synchronized* 关键字
- look at this intrinsic lock/monitor lock 内部锁 监视器锁



#### How to ensure thread-safe

操作原子化/使用锁

we must **make the operations atomic** to work with multiple threads. In Java, the first way to make that is to **use a lock**. All Java objects contain intrinsic locks

## Synchronized

- 对method synchronized to acquire the lock
- 在method内 synchronized(this)
- synchroniezed 某个 object
- if 方法为static
  - the used lock is the Class object.
- syn作用的对象是调用这个方法的对象，作用范围是函数

#### Intrinsic lock

- make methods atomic
- when thread has a lock, no other thread can acquire it
- only one method will be executed at the same time but the same method

#### 替代锁的方法：

use an other object just as a lock

### Fully Synchronizing objects

- a class in which every method is synchronized
- conditions: ready/active/waiting



### Synchronized VS volatile

volatile修饰变量，synchronized可以修饰方法和语句块

- a primitive variable may be declared **volatile**易变的
- an access to a volatile variable never has the potential to block: we're only ever doing a simple read or write;
  Unlike a synchronized block we will never hold on to any lock;



### 相同锁的同步方法

Java synchronized keyword is **re-entrant** in nature
一个同步方法调用另一个锁相同的同步方法，可以不获取锁而进入另一个方法
» Counter is used

### Limit of synchronized keyword 

it can only be used to control access of shared object within the same JVM

#### Overlapping: 

two threads read the same resource does not cause problems, multi threads want to read the resource are granted access

#### Summary

Individual code blocks within a method can be synchronized using

`synchronized(someObject)`//someObject is often this

a synchronized method is equivalent to a non-synchronized method with all its code enclosed by `synchronized(this)`



# Thread Synchronization

## Mutual exclusion

- supported by **object locks**, enables multiple threads to independently work on shared data without interfering with each other.

## Cooperation

-  supported by the **wait and notify methods of class Object**, enables threads to work together towards a common goal.

## Monitor

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201218224540641.png" alt="image-20201218224540641" style="zoom:80%;" />

- sleeping threads are shown as light grey circles

  active threads-dark grey

- If no other thread is waiting in the entry set and no other thread currently owns the monitor, the thread acquires the monitor and continues executing the monitor region.

- When the thread finishes executing the monitor region, it exits (and releases) the monitor.

- The only way a thread can move forward and execute the monitor region is by **acquiring the monitor**

- The only way a thread can enter a monitor is **by arriving at the beginning of one of the monitor regions associated with that monitor.**

### Active Thread

- The active thread can release the monitor in either of two ways
  - it can complete the monitor region it is executing. If it **completes** the monitor region, it exits the monitor via the door five.
  - If it executes a wait command
    - releases the monitor and goes through door number three

### 流程

- wait in the entry set
- 等 owner完事
- 如果owner没有指定notify, entry set 和 wait set竞争
- 进入owner
- 若wait()
- 进入wait set
- 等待别人notify

### Wait

- If there is another thread currently claiming ownership of the monitor, the newly arrived thread must wait in the entry set, possibly along with other threads already waiting there.
- wait() 让此线程 **releases the monitor**，进入monitor的wait set
- a thread that currently owns the monitor can **suspend** itself inside the monitor by executing a wait command.

### Notify

a thread execute notify, it continues to own the monitor until it releases the monitor of its own accord, either by executing a wait or by completing the monitor region.

### compete

- If a thread from the entry set wins the competition, it passes through door number two and becomes the new owner of the monitor.
- If a thread from the wait set wins the competition, it exits the wait set and reacquires the monitor as it passes through door number four.

### notifyall

- marks all threads currently in the wait set for eventual resurrection.

#### How to select thread from wait/entry

- a thread from the wait set given a notify command
- the order to resurrect threads from the wait set given a notify all command
- the order to allow threads from the entry set to acquire the monitor
- how to choose between threads suspended in the wait set versus the entry set after a notify command

### Note:

- wait/notify are placed in synchronized code
- suspend itself(sleep) with wait() when cannot continue
- wait: cause the thread to give up its lock/go to sleep/add it to the wait set
- 用 while循环不用if



# Week3-Day1

# Security Concepts for Middleware and Web Vulnerabilities漏洞

## Security Concepts of middleware

- Authentication mechanisms and credential management
- Authorization and access control management
- Shared data security and integrity
- Secure one-to-one and group communication
- Heterogeneous security/environment requirements support
- Secure mobility management
- Capability to operate in devices with low resources
- Automatic configuration and management of these facilities

### Loosely coupled connectivity

- Using http hypertext transport protocol超文本传输协议
- Multiple clients and servers interact independently
- Distributed connections

## Methods of securing web services

### Authentication认证

- Ensuring that it is the same person who she/he claims to be
- Method
  - Something one has
    - Credentials issued by a trusted authority such as **smart card**
  - Something one knows
    - **password**
  - Something one is
    - **Biometric information (fingerprint)**
- A strong authentication process consists of at least two of the above

### Authorisation授权

- Access control
  - Granting access to specific resources based on an authenticated user's entitlements
  - Entitlements are defined by one or several attributes.
    - An attribute is the property or characteristic of a user
      - Admin role, quest role, authorisation request, etc

### Confidentiality (保密)

- Privacy
- Keeping **information secretive**
  - reat web service request, email, identity of the sending and receiving parties in a **confidential manner**
  - To achieve **confidentiality and privacy**
    - Encrypt the content of a message
    - Do not reveal sending and receiving parties' identities
    - Use public key infrastructures (PKI) for encryption

### Integrity (一致性)

- Message in transit **should not be altered**
  - Sender should digitally sign the message.
  - A digital signature is used to validate the signature.
  - The timestamp in the signature prevents anyone from replaying this message after the expiration.
  - Exchanging security tokens in a trusted environment

# Layer of Security

## Transport-layer security

- **Secure Socket Layer (SSL)**, also known as Transport Layer Security (TLS)
  - **Authentication** between communicating two trusted parties
  - **Confidentiality** through data encryption
  - Message integrity by checking that the data is not corrupted
  - **Secure key exchange between client and server**

## Application-layer security

- Application-level security complements transport-level security
- Application-level security is based on **XML frameworks** defining confidentiality, integrity, authenticity; message structure; trust management and federation.
- **Data confidentiality数据保密** is implemented by **XML Encryption**.
  - XML Encryption defines how digital content is encrypted and decrypted, how the encryption key information is passed to a recipient, and how encrypted data is identified to facilitate decryption.
- **Data integrity and authenticity** are implemented by **XML Signature.**
  - XML Signature binds the sender's identity (or "signing entity") to an XML document. Signing and signature verification can be done using  symmetric or symmetric keys.

## Middleware-layer security

- Middleware layer security ensures that the **communicating security layers are secure**
- **Single Sign-On (SSO)** systems are used for authentication across the layers
- **Certificate-based SSO** are common in middleware security systems
- **Virtual organisation membership services (VOMS)** are used fore authentication/authorisation for different users belonging to different organisations

# Web Security Vulnerabilities (脆弱点)

- Web security Vulnerabilities are areas of weakness in web security that hackers or intruders exploit / access to systems

## Vulnerabilities

Injection flaws注入缺陷
- Injection flaws result from **failure to filter untrusted input**.
- It can happen when you pass unfiltered data to the SQL server (**SQL injection**), to the Lightweight Directory Access Protocol (LDAP) server (**LDAPInjection**), etc.
- The attacker can “**inject**” **commands to these entities**, resulting in loss of data and hijacking clients’ browsers.

Prevention
- Adopting **highly skillful programming** and **encryption techniques** plus **vigorous testing procedures**
- Updating browsers regularly



共九条：

破裂的验证：密码/URL不加密（使用tested framework）

Cross Site Scripting跨网站脚本攻击：简单输入/cookie to hacker（对输入数据清理）

Insecure Direct Object Reference：重置密码环境不安全，暴露密码（安全的重置环境）

Security Misconfigurations配置错误：密码使用默认，使用过期应用（自动执行安全配置）

Sensitive data exposure：不在tomcat安全tag时不使用SSL（使用ssl，加密应用）

Problem with access control level级别问题：执行正确验证系统失败（自动执行验证系统并确保一直在服务端）

Cross Site Request Forgery (CSRF)：进入第三方未验证网站（别进入url）

Unvalidated Redirects and Forwards：更换网址时经常redirect url（别在自己应用中redirect和forward URL）

#### 解决：都可以使用安全弱点扫描器 Web Security Vulnerability Scanners

#### Grid Security Infrastructure (GSI) in Globus

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201219003713672.png" alt="image-20201219003713672" style="zoom:67%;" />

#### Sign-On grid proxy init in Globus

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201219003826660.png" alt="image-20201219003826660" style="zoom:50%;" />

# IoT Protocols

## Representational State Transfer (REST)

- REST specification says that all interfaces must be **uniform** based on the concept of exchanging resources between the client and the server
- Communication should be **stateless** and **each request from client to server must contain all the information needed** (data, metadata, etc)

## IoT Protocols

### Representational State Transfer (REST)

- REST specification says that all interfaces must be uniform
- Communication should be stateless and each request from client to server must contain all the information needed

### IOT Protocols:

### HTTP-执行webapp的req和res功能

- Application level communication protocol
- It’s major function is to implement the **request and response functionalities** of **web applications**
- It is typically used in a **client-server applications**
- HTTPS: HTTP secure

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201219005001800.png" alt="image-20201219005001800" style="zoom:50%;" />

### TCP/IP-Internet交流

- Set of **computer networking communication protocols**
- It is used for **internet communications**
- It is an **end-to-end communication protocol**
  - Internet layer
    - Sends packets of data from the source network to single or multiple destination networks
    - use IP Address
    - The concept of sending packets of data across is known as “**packet routing**”
  - Transport Layer
    - It is a **connection-oriented end-to-end message transmission layer**
    - It provides reliable data transmission that
      - in the order
      - without error
      - failed, resent
      - flow control
      - no duplication
  - Application layer
    - This consists of other **application specific protocols**
    - FTP HTTP SMTP...

### UDP 传送transmit 视频，音乐等

User Datagram Protocol

- It is a **connectionless-oriented** communication transmission protocol
- Not reliable
- Transmitting data that **accuracy and reliability are not necessary**

### SOAP-作为web服务在web中交换结构数据

Simple Object Access Protocol

- It is a specification for **exchanging structured data** across the web as web services
- uses the **application layer protocols**
- uses the XML syntax
- good features
  - Neutrality中立性
  - Non-platform dependence
  - Scalability and extensibility

### FTP-转移transfer电脑数据从一个host到另一个host，通过tcp-based network

- File Transfer Protocol
- is a standard network protocol used to transfer computer files from one host to another host over a TCP-based network
- not secure

### SSH-Secure Shell-加密数据和交流/登录信息

- It is the most popular communication and login protocol for UNIX (Linux) systems
- It **encrypts data** and **communication/login information**
- It uses the **public key infrastructure (PKI) cryptography technology** for authentication
- use port 22
- eg Putty VNC WinSCP

### MQTT-提高网络通信在远程通信的网络带宽较差的地方

- Message Queue Telemetry Transport
- It is based on the **publish-subscribe messaging service model**
- It uses **brokers** that **publish messages**

### DDS-Data Distribution Service-在云系统中管理动态数据变化和通信

- This is a machine-to-machine (M2M) middleware standard
- managed by Object Management Group
- It enables **reliable exchange of data between heterogeneous systems** used by cloud service providers and subscribers
- It works on a **real-time basis** to manage **dynamic data exchange** and communication in cloud systems

### AMQP-Advanced Message Queuing Protocol

#### 使异构客户端hetetogeneous clients和服务器servers能够通信，使用点对点/发布订阅消息的方法

- MOM middlware protocol
- In enables heterogeneous clients and servers to communicate using **point-to-point** or **publish-subscribe** **messaging** methods

### RTPSP – Real Time Publish-Subscribe Protocol

实现多供应商multi-vendor DDS systems

- It is a **message oriented protocol**
- It works on **delivering real-time message exchange** services using the **publish-subscribe method**
- **Cloud-based messages** use RTPSP to exchange data between heterogeneous systems

### SSL/TLS-Secure Socket Layer/ Transport Layer Security 实现数据机密性confidentiality和完整性integrity

- These are **cryptographic protocols for secure communication over the internet**
- They use **digital certificates** for authentication
- They implement **data confidentiality** and **data integrity**

### NTP-Network Time Protocol 稳定分布式系统通信在network latency延迟的变化

- It is a **global networking protocol** for **synchronising time zone settings** on computer systems
- It **stabilises** the **variations in network latency** for distributed systems communicating with each other
- Not secure

### IMAP-Internet Message Access Protocol 确保user检索retrieve他们的邮件/for 数据存储

- This protocol enables users to **retrieve their emails and also for data storage**
- It is an **internet application layer** protocol
- allows **multiple users to simultaneously access the same mailbox**

### LDAP-Lightweight Directory Access Protocol 访问access分布式目录的信息服务

- It is an **application layer protocol**
- It used for **accessing distributed directory information** services over TCP/IP network
- most popular tools to **share and use information records**
- Is used to manage **large scale authentication** and **authorisation** systems for distributed **cloud** systems



### Bitcoin

an experimental, decentralized digital currency

Transaction: irreversible, cost little, fast

why: can but merchandise anonymously匿名购买商品

不需要额外费用，买来作为投资

管理：存储在数字钱包中，是一种虚拟银行账户

# Week3-Day3

# JavaScript

- dynamic programming language
- used for both client side and server side
- similar to PHP
- embed it in a HTML/use it with HTML
- syntax: how the language constructed

## Data Types

- Objects
  - They are written within curly braces ({})
  - `var student = {surName:”Wang”, firstName:”Liu”, age:20};`
  - Constructor
    - Creating objects with the “new” operator key word
    - The “new” key word must be followed by a **function invocation**
  - `var arr = new Array(); / var obj = new Object();`

- Boolean 
  
  `var value1=true;`
  
- typeof to get type
  
  - `typeof 23;//return a number`

## functions

```javascript
function fName (para1, para2) {
    return v;
}

e.g.华氏转换摄氏
function myCelsius(myFahrenheit) {
	return (5/9) * (myFahrenheit-32);
}
document.getElementById(“myDemo").innerHTML = myCelsius(32);
```

## DOM-Document Object Model

<img src="C:\Users\51615\AppData\Roaming\Typora\typora-user-images\image-20201219014327741.png" alt="image-20201219014327741" style="zoom:80%;" />

- getElementById()
  - Use this property to get the contents of the element
- innerHTML
  - **This method access an HTML element** via the id of the element
  - 属性

```html
<html>
    <body>
        <p id="myElement"></p>
       	<script>
         document.getElementById("myElement").innerHTML="Hello 			World!";
        </script>
    </body>
</html>
```

- Nodes

```html
<!--
Nodes:HTML Elements
e.g. Creating a new Node
-->
<div id="div1">
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>
<script>
    //create a new "p" element
    var para = document.createElement("p");
    //add text to "p", must create a text node first
    var node = document.createTextNode("This is new.");
    //append the text node追加文本节点
    para.appendChild(node);
    //find an existing element
    var element = document.getElementById("div1");
    element.appendChild(para);
</script>
```

- parent.removeChild(child);

- Nodes List

  - getElementsByTagName()

  - `var myNodeList = document.getElementsByTagName("p");`

    `document.getElementById(“myNodes").innerHTML = myNodeList.length;`

## Classes

- JavaScript classes are based on JavaScript **prototypes** and **inheritance**
- a class is a **set of objects** that **inherit properties** from the **same prototype object**
- function as a constructor

```html
<!DOCTYPE html>
<html>
    <body>
        <p id=“classExample"></p>
        <script>
            function Person(first, last, age) {
                this.firstName = first;
                this.lastName = last;
                this.age = age;
            }
            Person.prototype.nationality = “Chinese";
            var myFather = new Person(“ZHANG", “Wang", 18);
            document.getElementById("classExample").innerHTML = "My father is " + myFather.nationality;
        </script>
    </body>
</html>
```

## OOJSP  Object-Oriented JavaScript Programming

- 用 . 或者 [] 访问object的某个属性

  ```javascript
  var userObject = new Object();
  userObject.lastLoginTime = new Date();
  alert(userObject.lastLoginTime);
  ```

  

- Function as a constructor

  - ```javascript
    var func = new Function("x", "alert(x);");
    func(“My Third Function");
    ```

## IO in JS

- Input

  - Prompt提示符
  - stdln

- Output

  - alert
  - stdOut

- e.g.

  - ```javascript
    var strInput = WScript.StdIn.ReadAll();
    WScript.StdOut.Write(strInput)
    ```

## Cookies

- Cookies are **functionalities in web-browsers** that enable **data and information** about web activities to be **saved for future reference**
- 3 types of cookies
  - **Session cookies**
    - Created on the same browser that a user is using
    - Created to last for that session
  - **First party cookies**
    - Created on the same browser that a user is using
  - **Third party cookies**
    - Can be created by only a third party browser and not the current browser being used by the user

## jQuery

- jQuery is an JavaScript **cross-platform library and APIs**

- It is used to simply client-side programming with HTML

- used for: 

  Manipulating documents操作文档
  Selecting DOM
  Handling events

- consists

  - DOM element selections
  - DOM manipulation
  - Events
  - AJAX
  - JSON parsing

- `<script src="jquery.js"></script>`

- Basic syntax is: `$(selector).action()`

- ```javascript
  $(this).hide() - hides the current element.
  $("p").show() - show all <p> elements.
  $("p").fadein() - fade effects for all <p> elemens.
  
  Some API:
  add()
  .clearQueue()
  .click()
  .clone()
  ```

## JSON

- JavaScript Object Notation

- 特点：lightweight data-interchange format，sub-set of JS， language independent

- two structures
  - A collection of name/value pairs
  - An ordered list of values
  
- advantages:

  easily store anything, compact, maps very easily

- Where to use: in webapp/send data from the browser to the server

```html
<script type="text/javascript">
    var cart = {
        "orderID": 12345,
        "shopperName": "John Smith",
        "shopperEmail": "johnsmith@example.com",
        "contents": [
            {
                "productID": 34,
                "productName": "SuperWidget",
                "quantity": 1
            },
            {
                "productID": 56,
                "productName": "WonderWidget",
                "quantity": 3
            }
        ],
        "orderCompleted": true
    };
</script>
```

### Create and read JSON Strings from JS

- Create JSON string
  - JSON.stringify(*jsonvar*) 
- Read a JSON string
  - JSON.parse(*jsonstr*) 

### Create JavaScript to Display Dates

```html
<script>
    var currentDate = new Date(),
    day = currentDate.getDate(),
    month = currentDate.getMonth() + 1,
    year = currentDate.getFullYear();
    document.write(day + "/" + month + "/" + year)
</script>
```

## JS attributes

- Object Attributes

  - Every object has an associated prototype, class and extensible attributes

- Prototype attributes

  - This specifies the object from which it inherits properties

  - ```javascript
    var p={x:1}; // define a prototype object
    var o=Object.create(p); // create an object with that prototype
    p.isPrototypeOf(o); // => true: o inherits from p
    Object.prototype.isPrototypeOf(o); // => true: p inherits from Object.prototype
    ```

- Class Attributes

  - An object’s class attribute is a string that provides information about the type of of the object.

  - ![image-20201214002349443](C:\Users\Yubo\AppData\Roaming\Typora\typora-user-images\image-20201214002349443.png)

  - ```javascript
    Classof(null); // => “Null”
    Classof(2); // => “Number”
    Classof(false); // => “Boolean”
    Function f(); //=> “Window”
    ```

## RegExp

- A regular expression (RegExp) is an object that describes a pattern of characters
- `var pattern=new RegExp(“t$”);`
- `var re = /ab+c/;`

### rules

#### 匹配

- [...] 任意一个
- [^...] 非任意一个
- . 任意
- \d ASCII digit [0-9]
- \*  任意

#### 重复

- \+ 1或多个
- {n, m} n到m次 闭
- {n,} 大于等于n
- {n} 等于n次
- ？ 可选

### RegExp object

- methods

  - exec()
    - execute on the string to match the pattern
  - test()
    - takes a string argument and returns true if the string is in the pattern else false

- Modifier

  - pattern = /java/*modifier*;

  - /java/i

  - | Modifier | Description                       |
    | -------- | --------------------------------- |
    | g        | Perform a global match            |
    | i        | Perfoam case-insensitive matching |
    | m        | Perform multiline matching        |

# OSGI

## Terminologies

- Component
  - A web resource, web service, module or software package that communicates with other interacting components using its interface
  - Modular and cohesive implementation of services
- Bundles
  - OSGi components implemented by OSGi developers
  - A complete component software that can operate on its own
  - An embedded software that is shipped with hardware or other applications
- Modules
  - Comes from modular programming concept
  - The implementation of a particular functionality of a program
  - Other modules or parts of the program can call it using its interface if they implement acceptable interface rules to each other
- Services
  - Comes from service-oriented programming concept
  - Reusable functionalities of software instances using service-oriented architecture and interfaces

