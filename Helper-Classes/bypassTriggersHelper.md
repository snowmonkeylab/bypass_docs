---
layout: default
---
# bypassTriggersHelper

This class contains the core bypass processing logic. It queries 'Bypass Configuration' metadata records, processes the ruleset
and returns an instace of the [bypassTriggerWrapper](./bypassTriggerWrapper.md). This includes: (1) A boolean specifying whether the trigger should be exited
(2) A description of the applied bypass rule.


**See** [bypassTriggerWrapper](./bypassTriggerWrapper.md)


**Tests** [bypassTriggerHelperTest](../Test-Classes/bypassTriggerHelperTest.md), [bypassTriggerTestProxy](bypassTriggerTestProxy)


**Settings** The 'Bypass Settings' custom metadata type includes two settings used to control functionality in this class. Each can be enabled/disabled: (1) Debug logs - determines whether debug logs are included when the class is executed (2) Platform Events - when enabled, a platform event is logged to the 'Bypass Trigger' event channel each time an automation is skipped. In turn, this can be consumed by a Flow or off-platform to define robust logs and/or notifications


**Group** Helper Classes

## Methods
### `public static bypassTriggerWrapper bypassTrigger(String sObjectAPIName, String triggerName)`

Constructor. This method can be called from an Apex Trigger to query and execute Bypass Rules. Returns an instance of a [bypassTriggerWrapper](./bypassTriggerWrapper.md). Additionally this constructor is wrapped by the [bypassTriggersInvocable](../Invocable-Classes/bypassTriggersInvocable.md) class, exposing the method as a Flow Action.

#### Parameters

|Param|Description|
|---|---|
|`sObjectAPIName`|The API name of the triggering Salesforce object. For example Account or Custom_Object__c. Used to query and validate bypass rules|
|`triggerName`|The name of the triggering Apex Trigger or Flow. This provides context to the response, debug logs and platform events (if enabled in the Bypass package settings)|

#### Returns

|Type|Description|
|---|---|
|`bypassTriggerWrapper`|An instance of a [bypassTriggerWrapper](./bypassTriggerWrapper.md) class: a boolean determining whether the trigger or flow should be exited, a reason/descriptor|

#### Example
```apex
bypassTriggersHelper.bypassTrigger('Opportunity', 'opportunityTriggerHandler');
```


### `public static bypassTriggerWrapper bypassTriggerSimulate(String sObjectAPIName, String triggerName, String userId)`

Constructor. This method performs the came calculation as the previous constructor. It can be used to simulate bypass rule scenarios. To do this it allows provides an additional userId input - allowing for the simulation of bypass rulesets for a specific Salesforce user. Additionally, this constructor is wrapped by the [bypassTriggersSimulateInvocable](../Invocable-Classes/bypassTriggersSimulateInvocable.md) class, exposing the method as a Flow Action.

#### Parameters

|Param|Description|
|---|---|
|`sObjectAPIName`|The API name of the triggering Salesforce object. For example Account or Custom_Object__c. Used to query and validate bypass rules|
|`triggerName`|he name of the triggering Apex Trigger or Flow. This provides context to the response, debug logs and platform events (if enabled in the Bypass package settings)|
|`userId`|The Id of the Salesforce User for which the Bypass rules should be simulated|

#### Returns

|Type|Description|
|---|---|
|`bypassTriggerWrapper`|An instance of a [bypassTriggerWrapper](./bypassTriggerWrapper.md) class: a boolean determining whether the trigger or flow should be exited, a reason/descriptor|

#### Example
```apex
bypassTriggersHelper.bypassTriggerSimulate('Opportunity', 'opportunityTriggerHandler','005***************');
```


### `public static bypassTriggerWrapper bypassCalculation(String sObjectAPIName, String triggerName, String userId)`

This method is called each of the constructors. It performs the key logic to evalate and apply bypass rules: First, it queries Bypass Rules from the 'Bypass Configuration' Custom Metadata type. Each active rule is considered to determine whether a trigger or flow should be skipped. The 'Limit To - User' and 'Limit to - Object' Custom Metadata types are combined to refine the full scope of the configuration/rule. An active configuration with no additional limits results in all triggers being skipped. Those with object('s) defined are limited to triggers from that context. Those with a specific user('s') defined are limited to triggers from that user. Those with object('s') and user('s') are limited to the specified combination.

#### Parameters

|Param|Description|
|---|---|
|`sObjectAPIName`|The API name of the triggering Salesforce object. For example Account or Custom_Object__c. Used to query and validate bypass rules|
|`triggerName`|he name of the triggering Apex Trigger or Flow. This provides context to the response, debug logs and platform events (if enabled in the Bypass package settings)|
|`userId`|The Id of the Salesforce User for which the Bypass rules should be simulated|

#### Returns

|Type|Description|
|---|---|
|`bypassTriggerWrapper`|An instance of a [bypassTriggerWrapper](./bypassTriggerWrapper.md) class: a boolean determining whether the trigger or flow should be exited, a reason/descriptor|

### `public static String createDescription(Id bypassConfiguration, Map<Id,Bypass_Configuration__mdt> configurations, String eventTrigger, String userId)`

This method is called by the bypassCalculation() method. It formats the descriptor/reason a Bypass Rule was applied, creating a readable output that can be included in the [bypassTriggerWrapper](./bypassTriggerWrapper.md) response. Creates a pipe-seperated list of each applied Bypass Rule Id, Rule Name, Trigger Name and Bypass Reason

#### Parameters

|Param|Description|
|---|---|
|`Id`|The Bypass Configuration metadata record Id|
|`configurations`|A map of all active Bypass Configurations. Provides the ability to reference metadata about the in scope Bypass Configuration - to return related values as part of the reason or description|
|`eventTrigger`|The name of the originating trigger or flow|
|`userId`|The Id of the executing Salesforce User|

#### Returns

|Type|Description|
|---|---|
|`String`|A formatted bypass reason/description. Includes the Bypass Configuration Id, Name, the triggering automation and User Id|

### `public static List<Database.SaveResult> publishPlatformEvent(String eventDescription, String eventObject, String eventTrigger)`

This method is optionally called when platform events have been enabled in the Bypass Configuration Settings custom metadata. When enabled, this method publishes an event to the 'Bypass Trigger' events channel. In turn, events can be subscribed to via Flow or off-platform to create robust logging/notifications

#### Parameters

|Param|Description|
|---|---|
|`eventDescription`|The reason / description the Apex Trigger or Flow is being skipped|
|`eventObject`|The context e.g Opportunity, Case|
|`eventTrigger`|The name of the Apex Trigger / Flow|

#### Returns

|Type|Description|
|---|---|
|`List<Database.SaveResult>`|A list of save results - detailing the successes/failures for logged events|

---
