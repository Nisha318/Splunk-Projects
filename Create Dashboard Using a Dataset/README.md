
```bash
host=SplunkSrv01 backupduration=* domain=* | stats max(backupduration) by domain | head 5
```

![image](https://github.com/Nisha318/Splunk-Projects/assets/12909665/777b2c5f-338c-4a9c-bb1a-717db17a7bed)


<img src="https://github.com/Nisha318/Splunk-Projects/blob/main/Files/Splunk%20Dashboard%201.png">


## Create a Dashboard Prototype

### Cafe Sales - Highest Sales and Method of Order Placement 


```bash
| makeresults count=12 | streamstats count  | eval _time=_time-(count*3600) | eval drip =(random () % 3) + 1 | eval espresso =(random () % 3) + 1 | ev

```

![image](https://github.com/user-attachments/assets/7c3f7715-ff84-462d-bbac-ea94ffbdd8c9)


```bash
| makeresults count=3 | streamstats count
| eval host = case(count=1, "www1", count=2, "www2", count=3, "www3", count=4, null())
| eval 406 = case(count=1, 25, count=2, 39, count=3, 31, count=4, null())
| eval 500 = case(count=1, 25, count=2, 39, count=3, 31, count=4, null())
| eval 503 = case(count=1, 25, count=2, 39, count=3, 31, count=4, null())
| table host, 406, 500, 503'
```

![image](https://github.com/user-attachments/assets/9b87d572-8948-4fc9-9c28-213ac46c546d)




## User Data and Game Sales with Server Health Annotations

```bash
index=webapp sourcetype=app_monitoring | eval annotation_label = message | eval annotation_color = case(message="INFO maintenance operation", "#75C5F0", message="CRITICAL security issue", "#FF4747", message="WARNING network issue", "#F3CC17") 

```

![image](https://github.com/user-attachments/assets/f55ede8d-8f4a-4fba-97a4-32e2e2b6de28)


Dashboard for Game Sales and Web Server Errors

![image](https://github.com/user-attachments/assets/2e253ea7-ebd5-4299-bbeb-f02c89627853)



## IP Locations


![image](https://github.com/user-attachments/assets/f33bb63a-8d1c-43a5-b38b-04f8aeb2cc44)



![events sales visualizations](https://github.com/user-attachments/assets/960174c9-d0e2-4b1b-a35f-09b02b9b1b83)





![average bandwidth](https://github.com/user-attachments/assets/4e7a9594-9b0f-46c0-b1c5-8b678e95515b)




![Weekly Info](https://github.com/user-attachments/assets/045a77b3-d4b5-4a3b-8c9e-863b01a6213f)


Active Directory Event Logging

![1](https://github.com/user-attachments/assets/c0524310-cc76-4b76-9c2c-57b68aa250f3)


![2](https://github.com/user-attachments/assets/3dba249c-12c6-436e-8f5e-945e3e65dfad)


![3](https://github.com/user-attachments/assets/86433db8-49c5-4175-b1e2-f43a2ea37c7d)

![4](https://github.com/user-attachments/assets/32b1e231-a2a0-41f2-a2ad-e0e8c1ae01be)


![5](https://github.com/user-attachments/assets/0ec596c9-6fdf-40db-bed9-2792e90f8082)


VPN Login and Logout Activity Over Time

![image](https://github.com/user-attachments/assets/8fe4d1a0-13ed-44bb-a68a-4713e30fc723)



