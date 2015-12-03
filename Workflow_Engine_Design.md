The reference implementation of the business rule engine along with business process management engine/ workflow engine can be found at

http://www.flyingtroika.com/solutions/rule-engine and
http://www.flyingtroika.com/solutions/workflow-engine

Business rule engine reference implementation can be used as a library or
as a complete solution which can provide a full set of APIs for not only for business rule management but for workflow / business process management as well.
For example workflow engine delivers runtime execution, workflow engine template design, workflow persistence when its used as a platform. More details can be found at http://www.flyingtroika.com/solutions/workflow-engine help documentation for troika workflow engine.

Same thing is for rule engine, when its used as the platform from http://www.flyingtroika.com/solutions/rule-engine it delivers a full set of APIs and application layers for business rule management.
One of the major advantages of the http://www.flyingtroika.com/solutions/workflow-engine and http://www.flyingtroika.com/solutions/rule-engine from FlyingTroika is that it provides a seamless integration between different business engines like workflow, rule, complex event processing, machine learning lifecycle.
Another feature of the business process management  and business rule management is that both are working withing a single platform and allows easy to scale to working under high load of workflow activities execution or rules execution in runtime.

###### Business Process Framework, Workflow Engine, Workflow Process, Open Source Workflow Engine, Business Process Management, Workflow Development, Workflow Monitoring, Java Workflow Engine, BPM, Workflow Engine Library, Java Workflow Development, Complex Even Processing, CEP, Open Source Rule Engine, Algorithmic Trading Platform, Algorithmic Trading Engine, Complex Even Processing Engine, Business Process Management Design, Business Process Execution, Business Process Management System,  Service Oriented Architecture, Business Analytics, Business intelligence ######


---





# Introduction #

For the latest workflow engine development in java updates please see
workflow engine page http://code.google.com/p/troika/wiki/Workflow_Engine - workflow engine design, development, coding in java

Goal:

  * Implementation of Workflow Framework.
  * Easy integrate to different Wokrflow Engines
  * Import/Export Features as standard format
  * Impl of Basic functionality - Activities, Process Definition, Workflow Definition, Tasks, Security, etc...
  * Module based architecture in order to provide Open Framework for Open PLM/ERP/Finance systems.


---

# Workflow Engine Definition #

Workflow definition is following the common workflow design principals.
Having said that the workflow process is defined as a process which has flow of activities managed by the wokflow data - Object, users, transitions states.

The workflow process at runtime has several states such as: Initiated, Running, Suspended, Terminated, Complete.
```
initiated - process instance has been created

running - process in execution

suspended - temporarily  is stopped, inactive

complete - done execution

terminated - execution was stopped due to some issues
```



The workflow activity at runtime has also the following states as: Active, Inactive, Executed with some deviation.

The common object that can be defined as any document, user or even process itself can be identified by workflow, object lifecycle (states), complex object events. Of course it depends on the object type but as general object is driven by the process. The complex events are triggered by object behavioral activities  - workflow activities and defined by object lifecycle states. In addition to that for the intelligent execution all events, states, activities are managed by machine learning engine (for more info about machine learning engine please check the ML design page)


---

# Development Environment #

> GWT 2.0/Eclipse 3.5 is the development environment. Please see link http://code.google.com/webtoolkit/download.html
List of libraries that are used:
> - http://code.google.com/p/gwt-diagrams/ Diagrams Feature
> - http://code.google.com/p/gwt-dnd/ Drag And Drop Features
> - Using Google Protocol Buffers



---


## Implementation Design ##

For more details about CEP engine (open source complex event engine in java) and for latest stable release for CEP engine, workflow engine,rule engine see http://code.google.com/p/troika/wiki/Complex_Event_Processing_Engine


Need to define an interface for an object that listens for Workflow Events - such as WorkflowEventListener. Define to delegate impl for managing event listeners (Factories)


iWorkflow Engine - has following impl classs

WFProcess
WFTask
WFActivity
WFRoute
WFManager


We can create singleton class to manage add and removal functions of WorkflowEventlisteners (WokrflowEventManager based on Workflow Event Types).

```
public class TaskQueueManager
{
    // using single LinkList or double LinkList
    private LinkedList p_queue = new LinkedList();
....
```

Based on workflow implementation it is required to create the User and system based Workflow Tasks depends from business specifications

Support Workflow Standard to be able to easy Import/Export Workflows into different systems.

#### Rules Engine Integration ####
Integration with common definitions such as: RuleML, W3C Rules, SWSI and SWSL

### Lifecyle Engine Integration ###
Integration Concepts of RuleEngine, WorkflowEngine, LifecycleEngine
Building BI Framework (Business Intelligence Framework)- integration of RuleEngine, WorkflowEngine, LifecycleEngine


---

## Workflow Process Management ##
As Workflow main class implementation most refers to Workflow Template. As requirement - need create Workflow Process implementation - which will be responsible for running/management current Workflow processes (can call it WorkflowProcessManager and WorkflowProcess). some of the required attributes will be Principals (as individual assignee User or Group of Users)

  * Workflow Activity or WFTask
Can define name for single Node within Workflow (better call it WF Template)- Workflow Activity - means single Task or Activity which Principal (User) need execute/perform/do (etc...list of required by user actions in real world).

  * Can have what how many like WTActivities within Workflow Temlate, and it means within Workflow Process (something what is running currently). Also it mean that need implement WF Queue to handle multiple WFActivities for single user etc...

  * Workflow Activity routing
As Tasks (Workflow Activity) which are assigned to signle User/Group after execution need be routed to the next Activity - requires some Rootuing /Transitin capabilities such as implementation of Routing procedures. Routing - flexible, user defined in Workflow (Template) abilities to go to the next Tasks/ Activity based on certain conditions - for instance Tasks executed - go to the next Task. It can be done by defining Transitions such as Routing links: Task finished, Next Task, Reassign Task, Wait Decision Task, etc...

  * Workflow condition Robots
As Routings/Transitions represent ability to go to the Next Task (Running Workflow Process) / Ativity (in Workflow Template) need implement some condition handlers which can be called as Robots (need to have based list of robots such as Synchronization Robot, Timer Robot, Condition Robot, Notofication Robot - and etc, very important to have Abstract clasess and Interfaces for this implementation)

  * Workflow Task Actitivties Queue Management
Need to develop support for Background Queue Task handling. Due to the heavy load there is a case when it is required to offload tasks execution to the background task queue manager.
Probably need to have several Queue Managers which can be based on the type of Task activity that was submitted for execution.

---


---

## WF in Clustered Environment ##

Have to take under consideration the clustered deployment environment. It might be good to review  Terracota http://www.terracotta.org/web/display/docs/Home] as possible solution. There are good ideas there that can be useful.

---

## WF Configuration ##
So far all configurations are going to plan text file. Just for simplicity use.

---

## WF Persistence ##

Workflow Persistence can have several interfaces such as using straight Hibernate implementation or iPersistence-Engine that we have to develop. Anyway have to provide several interfaces that can connect through and process different events like store, update, delete, etc.
Java package -  Persistence should be the primary package for these API. Implementation goes to extra package that is called Impl. So we are going to have uniq persistence providers.

---


---

## WF Process Template Management ##

## Process Editor ##
One of the concept of process Editor is ability to create Workflow Process Template using graphical interface. it might be a good choice to use GWT. Process editor should provide capability of creating new Process Template, updating existed Process Template, managing the History of Process Template changes.

### WF Workflow File Format ###

WF Format is XML based file or files that can be enveloped into Jar/Zip Archive.

## WF Process Template Version History Management ##
There is a need to have a common workflow database online that users will be able to submit worklfow template to the global community (as service)

---


---

## WF Datastore - Persistence ##

Need to develop simple ORM for workflow persistence to DBs.
So far MySQL is the primary Database and all sql should be executed under MySQL without any issues. Other DBs can be taken under considerations namely ORM interaction is going to be under iPersistence-Engine and it is based on certain DB constraints.

---


## Workflow execution in a Cloud Space ##

In order to support distributed wf deployment and wf execution Cloud infrastructure should be taken under consideration. There are several options that have to be available. For example deployment to SaaS Cloud Platforms like Amazon Webservices and local/remote deployment/configuration using Hadoop. Primary the 1-st step is to design workflow architecture on top of Hadoop framework so WF APIs will be opened enough by other engines/applications/frameworks and software models when wf engine is configured to use Hadoop and big table non db data-stores.

###### Business Process Framework, Workflow Engine, Workflow Process, Open Source Workflow Engine, Business Process Management, Workflow Development, Workflow Monitoring, Java Workflow Engine, BPM, Workflow Engine Library, Java Workflow Development, Complex Even Processing, CEP, Open Source Rule Engine, Algorithmic Trading Platform, Algorithmic Trading Engine, Complex Even Processing Engine, Business Process Management Design, Business Process Execution, Business Process Management System,  Service Oriented Architecture, Business Analytics, Business intelligence ######

###### Business Process Framework, Workflow Engine, Workflow Process, Open Source Workflow Engine, Business Process Management, Workflow Development, Workflow Monitoring, Java Workflow Engine, BPM, Workflow Engine Library, Java Workflow Development, Complex Even Processing, CEP, Open Source Rule Engine, Algorithmic Trading Platform, Algorithmic Trading Engine, Complex Even Processing Engine, Business Process Management Design, Business Process Execution, Business Process Management System,  Service Oriented Architecture, Business Analytics, Business intelligence ######