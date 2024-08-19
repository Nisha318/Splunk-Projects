## Using Fields

SecOps wants a list of authentication failure events associated with admin roles over the last 60 minutes

```bash
index=security sourcetype=linux_secure failed invalid user=admin*
```

![image](https://github.com/user-attachments/assets/583a0f22-c788-4f18-966f-9623bb06b940)


Events from online sales that encountered a server problem (status>399.) 

```bash
index=web sourcetype=access_combined action=purchase status>399 
| table clientip host status

```
![image](https://github.com/user-attachments/assets/1fe80009-d954-4dd9-9161-2d2fb16b51d8)


```bash
index=web sourcetype=access_combined action=purchase status>399 
| table clientip host status 
| rename clientip as "Customer IP", host as "Web Server", status as "HTTP Status"

```


![image](https://github.com/user-attachments/assets/d4cbf170-b501-4ac9-8eac-e1038ff49a27)




