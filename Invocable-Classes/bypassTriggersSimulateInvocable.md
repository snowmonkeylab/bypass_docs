---
layout: default
---
# bypassTriggersSimulateInvocable

Exposes the [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) simulate method as an invocable Flow action. Queries and runs bypass configurations (rules) from the 'Bypass Package' to return a [bypassTriggerWrapper](../Helper-Classes/bypassTriggerWrapper.md): (1) A boolean specifying whether the trigger should be exited (2) A description of the applied bypass rule.


**See** [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md)


**Tests** [bypassTriggerSimulateInvocableTest](bypassTriggerSimulateInvocableTest)


**Group** Invocable Classes

## Methods
### `public static List<Response> bypass(List<simulateRequest> requests)`

`INVOCABLEMETHOD`

Implements the invocable Apex syntax to call the [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) bypassTriggerSimulate(sObjectAPIName,triggerName,userId) method from a Flow context. Based on configured Bypass rules, returns whether the triggering Flow should be exited along with a reason/description.

#### Parameters

|Param|Description|
|---|---|
|`requests`|A list of the request class defined below. Passed from the triggering Flow. Includes the triggering Salesforce object Id, triggering flow name and requested sumulation userId as parameters.|

#### Returns

|Type|Description|
|---|---|
|`List<Response>`|A list of the response class defined below. This mirrors the [bypassTriggerWrappper](bypassTriggerWrappper) to provide a boolean determiner of whether the triggering flow should be exited and a reason/description based on the executed Bypass ruleset|

---
## Classes
### Response

Defines the outputs for the invocable Flow Action. Mirrors the variables returned by the [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) method used to query and exexture Bypass rules/configurations - an instance of the [bypassTriggerWeapper](bypassTriggerWeapper) class

#### Fields

##### `public bypassReason` → `String`

`INVOCABLEVARIABLE` 

##### `public bypassTrigger` → `Boolean`

`INVOCABLEVARIABLE` 

---

### simulateRequest

Defines the required inputs for the invocable Flow Action. Mirrors the variables required by the [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) method used to query and execute Bypass rules/configurations.

#### Fields

##### `public triggerName` → `String`

`INVOCABLEVARIABLE` 

##### `public triggerObject` → `String`

`INVOCABLEVARIABLE` 

##### `public triggerUserId` → `String`

`INVOCABLEVARIABLE` 

---

---
