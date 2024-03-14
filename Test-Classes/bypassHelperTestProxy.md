---
layout: default
---
# bypassHelperTestProxy

`TESTVISIBLE`

Custom Metadata is visible by test classes. As users can alter it at any time, this unfortunately provides an unreliable source for stable testing. This proxy is called by the [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md) when it is executed in a test context. This instantiates Custom Metadata values in memory - provding a de-coupled and reliable dataset to test against.


**See** [bypassTriggersHelper](../Helper-Classes/bypassTriggersHelper.md)


**Group** Test Classes

## Methods
### `public static List<Bypass_Configuration__mdt> proxyMetadata()`

Instantiates an in-memory Bypass configuration Metadata record. This is used as a stable data set by the [bypassTriggersHelperTest](bypassTriggersHelperTest)

#### Returns

|Type|Description|
|---|---|
|`List<Bypass_Configuration__mdt>`|An in memory Bypass_Configuration__mdt record. A global bypass configuration requiring all Flows and Apex Triggers are skipped|

### `public static List<Bypass_Settings__mdt> bypassSettings()`

Instantiates in memory Bypass_Settings__mdt records. This ensures that the optional 'debug log' and 'platform event' features are executed in a test context

#### Returns

|Type|Description|
|---|---|
|`List<Bypass_Settings__mdt>`|Two in-memory bypass setting metadata records - one enabling debug logs and the other platform events|

---
