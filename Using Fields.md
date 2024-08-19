## Using Fields

### SecOps wants a list of authentication failure events associated with admin roles over the last 60 minutes

Search for all failed logins containing username that begins with "admin"

```bash
index=security sourcetype=linux_secure failed invalid user=admin*
```

![image](https://github.com/user-attachments/assets/583a0f22-c788-4f18-966f-9623bb06b940)


### Events from online sales that encountered a server problem (status>399) over the last 4 hours



```bash
index=web sourcetype=access_combined action=purchase status>399 
| table clientip host status

```
![image](https://github.com/user-attachments/assets/1fe80009-d954-4dd9-9161-2d2fb16b51d8)

Renames clientip field to "Customer IP", host field to "Web Server", and status field to "HTTP Status"


```bash
index=web sourcetype=access_combined action=purchase status>399 
| table clientip host status 
| rename clientip as "Customer IP", host as "Web Server", status as "HTTP Status"

```


![image](https://github.com/user-attachments/assets/d4cbf170-b501-4ac9-8eac-e1038ff49a27)


### SecOps wants to see a count of event descriptions by port from all web server events over
the past 7 days.

Search web server events over the last 7 days that contain the keyword "port"

```bash
index=security sourcetype=linux_secure port
```

![image](https://github.com/user-attachments/assets/3a049c9d-c632-4870-bf28-3d4318a35192)


Extracts temporary fields and include events based on pattern matching
```bash
index=security sourcetype=linux_secure port
| erex event_description examples="Failed password , Accepted password "

```

![image](https://github.com/user-attachments/assets/873baae6-3ce9-47ba-9ef5-7e9eee042e68)


```bash

index=security sourcetype=linux_secure port 
|  erex event_description examples="Failed password , Accepted password " 
| stats count(src_port) by event_description
```

![image](https://github.com/user-attachments/assets/2f3faf08-ffe1-45ec-b3fe-caaece54947e)

Create a new field called "port" and provide it with 3 port examples, then count port values:

```bash

index=security sourcetype=linux_secure port 
| erex port examples="22,1229,1268"
| erex event_description examples="Failed password , Accepted password " 
| stats count(port) by event_description
```

![image](https://github.com/user-attachments/assets/07b42ddc-ff87-4a7f-af5a-7081d515ad32)


Replace 'erex' command with Splunk recommended 'rex' commands
```bash
index=security sourcetype=linux_secure port
| rex "(?i)0(?P<port>[^ ]+)"
| rex "(?i)^[^\]]*\]:\s+(?P<event_description>\w+\s+\w+)"
| stats count(port) by event_description

```
![image](https://github.com/user-attachments/assets/a0f52c80-32b2-4e26-a911-f6b9c2d4afb0)



![image](https://github.com/user-attachments/assets/0730068c-49a9-4d36-8645-111e3d21599c)
