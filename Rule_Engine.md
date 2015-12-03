#### Reference Implementation and Product for Rule Engine, Business Process Management ####
There is product implementation based on the design which can be found
at http://www.flyingtroika.com/ workflow engine and rule engine implementation.
# Introduction #

Rules Engine usage, design and implementation


# Details #
Execution chain of Business rules, integration of business rules with workflow activities, integration business rules with complex event processing - these are some of the main ideas behind our implementation which helps to streamline business process management and analyze business models.

Rule Engine persist data in a simple mode by rule object check sums (hash codes). There are two major types of rule models such as static model and real time model or sometime we call it execution rule engine model. If for example we have a set of rules that we would like to execute at some point or event or associate this execution to workflow activities or expression  - this can be done by static rule model. the further execution will be done though rule pipeline and int/out rule data will be persisted in a simple mode timestamp plus rule object check sums. As a result we get a model which is simple enough to use in different use cases - rule hashtable (just rule hashcode - LinkedHashSet implementation)

Rule model is a java class with certain constraints. Having rule to be define though java classes helps to create rules in a simple way. though rule priorities have to be set manually.

### Rule Engine Design ###

  1. Rule engine definition - based on plain java object
  1. Execution of the rules should be managed by scheduler (different scheduling algorithms to use), each rule has own priority of execution and timing constraints
  1. Rules execution is persisted so we can reload the entire rule execution history; import and export interfaces
  1. support distributed rule execution, distributed persistence
  1. rule inference logic resolution, rule set flow
  1. rule engine should be able to execute as a standalone engine or a part of business application, so integration apis are very important; rule engine should be extensible and easy configurable using a specific types of configurations (dependency inject support, rest web services)

### Rule engine persistence ###
http://code.google.com/p/troika/wiki/Rule_Engine_Persistence

### Rule  engine design ###
http://code.google.com/p/troika/wiki/Rule_Engine_Design

### Rule engine execution ###
http://code.google.com/p/troika/wiki/Rule_Engine_Runtime

###### Business Process Framework, Workflow Engine, Workflow Process, Open Source Workflow Engine, Business Process Management, Workflow Development, Workflow Monitoring, Java Workflow Engine, BPM, Workflow Engine Library, Java Workflow Development, Complex Even Processing, CEP, Open Source Rule Engine, Algorithmic Trading Platform, Algorithmic Trading Engine, Complex Even Processing Engine, Business Process Management Design, Business Process Execution, Business Process Management System,  Service Oriented Architecture, Business Analytics, Business intelligence ######

Good coverage of implemented APIs can be found under

> http://flyingtroika.com/solutions/rule-engine and
> http://flyingtroika.com/solutions/workflow-engine


The reference implementation of the business rule engine along with business process management engine/ workflow engine can be found at

http://www.flyingtroika.com/solutions/rule-engine and
http://www.flyingtroika.com/solutions/workflow-engine

Business rule engine reference implementation can be used as a library or
as a complete solution which can provide a full set of APIs for not only for business rule management but for workflow / business process management as well.
For example workflow engine delivers runtime execution, workflow engine template design, workflow persistence when its used as a platform. More details can be found at http://www.flyingtroika.com/solutions/workflow-engine help documentation for troika workflow engine.

Same thing is for rule engine, when its used as the platform from http://www.flyingtroika.com/solutions/rule-engine it delivers a full set of APIs and application layers for business rule management.
One of the major advantages of the http://www.flyingtroika.com/solutions/workflow-engine and http://www.flyingtroika.com/solutions/rule-engine from FlyingTroika is that it provides a seamless integration between different business engines like workflow, rule, complex event processing, machine learning lifecycle.
Another feature of the business process management  and business rule management is that both are working withing a single platform and allows easy to scale to working under high load of workflow activities execution or rules execution in runtime.

#### References ####

  1. http://en.wikipedia.org/wiki/Rete_algorithm
  1. http://en.wikipedia.org/wiki/Business_rules_engine
  1. http://en.wikipedia.org/wiki/Business_Rule_Management_System
  1. http://en.wikipedia.org/wiki/Business_process_management
  1. http://www.flyingtroika.com/solutions/rule-engine