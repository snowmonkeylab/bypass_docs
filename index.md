---
layout: default
---
# Classes
## Test Classes

### [bypassHelperTestProxy](./Test-Classes/bypassHelperTestProxy.md)

Custom Metadata is visible by test classes. As users can alter it at any time, this unfortunately provides an unreliable source for stable testing. This proxy is called by the [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md) when it is executed in a test context. This instantiates Custom Metadata values in memory - provdi&hellip;


### [bypassTriggerHelperTest](./Test-Classes/bypassTriggerHelperTest.md)

Test class for [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md) and [bypassTriggerWrapper](./Helper-Classes/bypassTriggerWrapper.md). test.isRunningTest is used in the [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md) class to call the [bypassHelperTestProxy](./Test-Classes/bypassHelperTestProxy.md) when running in a test context. This simualtes custom metadata values in memory. All tests are run against mocked, in-memory v&hellip;


### [bypassTriggerInvocableTest](./Test-Classes/bypassTriggerInvocableTest.md)

Test class for [bypassTriggerInvocable](bypassTriggerInvocable) and [bypassTriggerSimulateInvocable](bypassTriggerSimulateInvocable). Creates a list of invocable requests and validates that a correct response is received from the [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md)


## Helper Classes

### [bypassTriggerWrapper](./Helper-Classes/bypassTriggerWrapper.md)

Defines the response structure used by the [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md) class when Bypass Configurations are queried and executed



### [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md)

This class contains the core bypass processing logic. It queries 'Bypass Configuration' metadata records, processes the ruleset
and returns an instace of the [bypassTriggerWrapper](./Helper-Classes/bypassTriggerWrapper.md). This includes: (1) A boolean specifying whether the trigger should be exited
(2) A description of the applied bypas&hellip;

## Invocable Classes

### [bypassTriggersInvocable](./Invocable-Classes/bypassTriggersInvocable.md)

Exposes the [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md) method as an invocable Flow Action. Queries and runs bypass configurations (rules) from the 'Bypass Package' to return a [bypassTriggerWrapper](./Helper-Classes/bypassTriggerWrapper.md): (1) A boolean specifying whether the trigger should be exited (2) A description of the applied bypass rule.



### [bypassTriggersSimulateInvocable](./Invocable-Classes/bypassTriggersSimulateInvocable.md)

Exposes the [bypassTriggersHelper](./Helper-Classes/bypassTriggersHelper.md) simulate method as an invocable Flow action. Queries and runs bypass configurations (rules) from the 'Bypass Package' to return a [bypassTriggerWrapper](./Helper-Classes/bypassTriggerWrapper.md): (1) A boolean specifying whether the trigger should be exited (2) A description of the applied bypass rule&hellip;

