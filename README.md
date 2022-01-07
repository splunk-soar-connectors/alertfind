[comment]: # "Auto-generated SOAR connector documentation"
# AlertFind

Publisher: Splunk Community  
Connector Version: 2\.0\.3  
Product Vendor: Aurea  
Product Name: AlertFind  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.0\.0  

Integrate with AlertFind to enable notification actions

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a AlertFind asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**url** |  required  | string | AlertFind instance URL
**username** |  required  | string | AlertFind username
**password** |  required  | password | AlertFind password

### Supported Actions  
[test connectivity](#action-test-connectivity) - Checks authentication with the AlertFind instance  
[send notification](#action-send-notification) - Send notification to AlertFind  
[cancel notification](#action-cancel-notification) - Cancel the sending of a notification  
[notification status](#action-notification-status) - Check the status of a notification  
[recipient status](#action-recipient-status) - Check the recipient status of a notification  

## action: 'test connectivity'
Checks authentication with the AlertFind instance

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'send notification'
Send notification to AlertFind

Type: **generic**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**team** |  required  | AlertFind team associated to this notification | string |  `alertfind team` 
**notification\_subject** |  required  | Subject of notification | string | 
**notification\_body** |  required  | Body of notification | string | 
**response\_descriptions** |  required  | Comma separated list of allowed responses | string | 
**max\_response\_recipients** |  optional  | Maximum number of recipients allowed to respond with each response | numeric | 
**recipient\_ids** |  required  | Comma separated list of IDs of recipients | string | 
**recipient\_type** |  required  | Type of recipients for the notification | string | 
**recipient\_delay** |  optional  | Time \(ms\) to delay after notifying each recipient | numeric | 
**delay** |  optional  | Time \(ms\) to delay sending of the notification | numeric | 
**stop\_on\_response\_limit** |  optional  | Stop notifying recipients after response limit is reached | boolean | 
**authenticate** |  required  | Require recipients to authenticate when responding | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@id | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\#text | string |  `alertfind notification` 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@soapenc\:root | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@xmlns\:soapenc | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@soapenv\:encodingStyle | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:sendNotificationResponse\.result\.\#text | string |  `alertfind notification` 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:sendNotificationResponse\.result\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsd | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsi | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:soapenv | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:sendNotificationResponse\.result\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:sendNotificationResponse\.\@xmlns\:ns1 | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:sendNotificationResponse\.\@soapenv\:encodingStyle | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
action\_result\.summary\.notification\_id | string |  `alertfind notification` 
action\_result\.parameter\.team | string |  `alertfind team` 
action\_result\.parameter\.delay | string | 
action\_result\.parameter\.authenticate | boolean | 
action\_result\.parameter\.recipient\_ids | string | 
action\_result\.parameter\.recipient\_type | string | 
action\_result\.parameter\.recipient\_delay | string | 
action\_result\.parameter\.notification\_body | string | 
action\_result\.parameter\.notification\_subject | string | 
action\_result\.parameter\.response\_descriptions | string | 
action\_result\.parameter\.stop\_on\_response\_limit | boolean | 
action\_result\.parameter\.max\_response\_recipients | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'cancel notification'
Cancel the sending of a notification

Type: **generic**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**notification** |  required  | ID of notification to cancel | string |  `alertfind notification` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@id | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@soapenc\:root | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@xmlns\:soapenc | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\@soapenv\:encodingStyle | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsd | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsi | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:soapenv | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:cancelNotificationResponse\.result\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:cancelNotificationResponse\.\@xmlns\:ns1 | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:cancelNotificationResponse\.\@soapenv\:encodingStyle | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
action\_result\.parameter\.notification | string |  `alertfind notification` 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'notification status'
Check the status of a notification

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**notification** |  required  | ID of notification to get the status of | string |  `alertfind notification` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@id | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.status\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.status\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.responses\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.responses\.responses\.\*\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.responses\.\@soapenc\:arrayType | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns2 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@soapenc\:root | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:soapenc | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@soapenv\:encodingStyle | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.count\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns3 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.abbreviation\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.abbreviation\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns4 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns5 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns6 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns7 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsd | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsi | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:soapenv | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryNotificationStatusResponse\.result\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryNotificationStatusResponse\.\@xmlns\:ns1 | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryNotificationStatusResponse\.\@soapenv\:encodingStyle | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
action\_result\.parameter\.notification | string |  `alertfind notification` 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'recipient status'
Check the recipient status of a notification

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**notification** |  required  | ID of notification to get the recipient status of | string |  `alertfind notification` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@id | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.name\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.name\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.response\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.response\.\@xsi\:nil | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.response\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.userName\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.userName\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.timestamp\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.timestamp\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:ns3 | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.statusCode\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@soapenc\:root | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.statusMessage\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.statusMessage\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@xmlns\:soapenc | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\@soapenv\:encodingStyle | string | 
action\_result\.data\.\*\.soapenv\:Body\.multiRef\.\*\.\#text | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsd | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:xsi | string | 
action\_result\.data\.\*\.soapenv\:Body\.\@xmlns\:soapenv | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.result\.result\.\@href | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.result\.\@xsi\:type | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.result\.\@xmlns\:ns2 | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.result\.\@xmlns\:soapenc | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.result\.\@soapenc\:arrayType | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.\@xmlns\:ns1 | string | 
action\_result\.data\.\*\.soapenv\:Body\.ns1\:queryRecipientStatusResponse\.\@soapenv\:encodingStyle | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
action\_result\.parameter\.notification | string |  `alertfind notification` 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 