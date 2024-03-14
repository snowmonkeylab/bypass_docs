---
layout: default
---
# bypassTriggerWrapper

`TESTVISIBLE`

Defines the response structure used by the [bypassTriggersHelper](./bypassTriggersHelper.md) class when Bypass Configurations are queried and executed


**See** [bypassTriggersHelper](./bypassTriggersHelper.md)


**Tests** [bypassTriggerHelperTest](../Test-Classes/bypassTriggerHelperTest.md)


**Group** Helper Classes

## Properties

### `public bypassReason` → `String`


Based on the executed Bypass Configuration. Specifies the reason the triggering Flow / Apex Trigger should be skipped or not skipped. For example - a global bypass (all Ape Triggers and Flows), object level bypass (for specified objects only), user bypass (for specified users only) or combination of object and user (for a specified combination of users and objects).

### `public bypassTrigger` → `Boolean`


Determines whether the triggering Flow/Apex Trigger should be exited

---
