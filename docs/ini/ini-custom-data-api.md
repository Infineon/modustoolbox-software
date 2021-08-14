# INI Custom Data API

# Overview

Custom Data refers to data that you can pass from your application to the Cirrent Agent. The various data types Custom Event (eg: user initiated reboot), or Custom Measurement (eg: CPU temperature), or Custom Attribute (eg: firmware version). This Custom data can be passed from your application to the Cirrent Agent (CA) using INI Custom Data API.

This document covers an example use case, requirements and general considerations for using the IoT Network Intelligence feature to add customer-defined data through an API call in the cirrent_cli. The data sent using this API will be accessible in the Cirrent Console.

## **Sending INI Custom data API using the cirrent_cli:**
```
$ cirrent_cli ini_custom <type> <name> <value>
```
### Arguments

The  cirrent_cli  call takes in three ordered arguments:

#### type

-   This case-sensitive string must be one of  event,  measurement,  attribute, or  state
    

#### name

-   This case-sensitive string must be  no longer than 100 bytes.
    

#### value

-   This string depends on what the data  type  is being sent. The following table describes the accepted  value  for each corresponding data  type
    

Choosing the right data to send:

| type | Accepted value |
| :----: | :-------------:|
event | start,  stop,  ““
measurement | floating point
attribute | string
state | string

**NOTE:**

1.  Dummy custom attribute and dummy custom event sent using cirrent_cli during testing will be visible on the console forever.
2.  Make sure the names of the custom attribute/event used during testing are meaningful and will be used in the future.

The Cirrent Agent 1.39.x versions support a maximum of 5 custom attribute, state, measurement, event each.

### Return Values

All  cirrent_cli ini_custom

stdout | stderr | Reason(s) |
| :----: | :-------------:|:----------------------:|
FAILURE | non-zero | <ul><li>More custom event types than preconfigured maximum sent</li><li>Out of storage</li><li>Cirrent Agent not running</li><li>Invalid arguments</li></ul> |
| OK | 0 | Cirrent Agent successfully received and stored ini_custom data |

**Example shell command:**
```
$ export LD_LIBRARY_PATH=/PATH_TO/cirrent/lib
```
**attribute:**
```
$ ./cirrent_cli ini_custom attribute fw_version 1.2
```
**state:**
```
$ ./cirrent_cli ini_custom state connection_established 1
```
**measurement:**
```
$ ./cirrent_cli ini_custom measurement cpu_temp 30  
$ ./cirrent_cli ini_custom measurement cpu_temp 20  
$ ./cirrent_cli ini_custom measurement cpu_temp 10  
$ ./cirrent_cli ini_custom measurement cpu_temp 40
```
This adds a custom measurement cpu_temp to the measurement summary along with the following information for cpu_temp

"average": 25, "sample_count": 4,"sampling_interval": 60,"max": 40,"min": 10, and standard_deviation

**NOTE:**

1.  Each custom measurement command should be executed at most 1 minutes apart and the measurement value should be an integer or a floating point.
2.  If a string is passed as a custom measurement, the average, max, and min for that measurement will be reported as 0
3.  Only continuous measurements are supported. At least one measurement should be sent every minute.

**event:**
```
$ ./cirrent_cli ini_custom event log_upload
```
This will add an event count of log_upload=1 to the event summary.
```
$ ./cirrent_cli ini_custom event log_upload_duration start  
$ ./cirrent_cli ini_custom event log_upload_duration stop
```
This will add an event count of log_upload_duration=(Duration in minutes between when the start and stop commands were executed) to the event summary.
