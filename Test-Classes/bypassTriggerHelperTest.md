---
layout: default
---
# bypassTriggerHelperTest

`ISTEST`

Test class for [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) and [bypassTriggerWrapper](../Helper-Classes/bypassTriggerWrapper.md). test.isRunningTest is used in the [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) class to call the [bypassHelperTestProxy](./bypassHelperTestProxy.md) when running in a test context. This simualtes custom metadata values in memory. All tests are run against mocked, in-memory values in order to de-couple test runs from user changeable custom metadata values. More nuanced control is provided by altering the 'triggerName' input variable - the in-memory data is only created when the trigger name is defined as 'Test Bypass All'.


**See** [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md)


**Group** Test Classes

## Methods
### `private static void triggerBypassRules()`

`ISTEST`

The [bypassHelperTestProxy](./bypassHelperTestProxy.md) defines a global bBypass Configuration - all triggers and flows should be excluded. This test method asserts that the correct response is received and that the description includes the correct custom label text

### `private static void triggerNoBypassRules()`

`ISTEST`

This test method uses the triggerName variable to ensure the [bypassHelperTestProxy](./bypassHelperTestProxy.md) is not executed. As a result, no custom metadata present in the test context. In turn, it asserts that the response instucts not to skip the execution of automation and that the description includes the correct custom label text

### `private static void triggerPlatformEvent()`

`ISTEST`

This test method asserts that a platform event can be successfully published to the Bypass Trigger event channel.

---
