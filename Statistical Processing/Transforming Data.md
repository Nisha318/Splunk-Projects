## Transforming Data

### The Network team wants to add a dashboard panel that displays internet usage over the last 24 hours.

Multi-Series Visualization Using Timechart

```bash
index=network sourcetype=cisco_wsa_squid
| timechart count by usage
```

![image](https://github.com/user-attachments/assets/5f076c13-5397-498a-814c-ae025d1820d8)


![image](https://github.com/user-attachments/assets/23a45951-c52d-4906-a23e-d6e958a2064a)


### Security wants to add a dashboard panel that displays the top 10 IPs associated with "Accepted" and "Failed" events on the web server.


```bash
index=security sourcetype=linux_secure vendor_action!="session opened"
| chart count by vendor_action src_ip
```

![image](https://github.com/user-attachments/assets/6731f547-0b8a-4000-aceb-d1abdbcbe823)


Remove "Other" Category

```bash
index=security sourcetype=linux_secure vendor_action!="session opened"
| chart count over vendor_action by src_ip useother=f
```

![image](https://github.com/user-attachments/assets/8045c9c5-e869-49e3-be64-cc013267140f)


![image](https://github.com/user-attachments/assets/fd4265f8-643d-4cf9-8581-6e93b1466136)


### Sales and Marketing want to know the two most popular referrer domains our website users are coming from.


```bash
index=web sourcetype=access_combined referer_domain!=http://www.buttercupgames.com
```

![image](https://github.com/user-attachments/assets/5cad11c9-86ff-4497-8b33-bb1e498efa87)

```bash
index=web sourcetype=access_combined referer_domain!=http://www.buttercupgames.com
| top limit=2 referer_domain
```


![image](https://github.com/user-attachments/assets/6bed68ee-c529-4dd6-a2f6-230497c920e1)

```bash
index=web sourcetype=access_combined referer_domain!=http://www.buttercupgames.com
| top limit=2 showperc=f referer_domain
```

OR

```bash
index=web sourcetype=access_combined referer_domain!=http://www.buttercupgames.com
| top limit=2 referer_domain
| fields - percent
```

![image](https://github.com/user-attachments/assets/ff9ab698-b022-4993-9966-edff0a204f43)


![image](https://github.com/user-attachments/assets/f32fc33d-78b7-4f7c-b53f-a7699cc282c3)


### Facilities needs to know how many people are accessing the Buttercup Games offices daily.

```bash
index=security sourcetype=history_access
| stats count by Address_Description
```

![image](https://github.com/user-attachments/assets/78a3a2d2-d8a0-4a31-a3cd-3041859477b0)

```bash
index=security sourcetype=history_access
| stats dc(Username) by Address_Description
```

![image](https://github.com/user-attachments/assets/2ff64f37-4377-45fc-927f-3a1729cd113d)

```bash
index=security sourcetype=history_access 
| stats dc(Username) by Address_Description 
| rename dc(Username) as "Badged-in Employees"
```

![image](https://github.com/user-attachments/assets/2c4fcea8-9609-4e6f-b86e-8d7b1ce6cfbd)

![image](https://github.com/user-attachments/assets/b7e40c02-0e8f-44b7-8838-4bc673408f32)


### Security wants to identify the types of content employees are viewing while on the network. Specifically, they want to know the rare content types as these can potentially be malicious. 

```bash
index=network sourcetype=cisco_wsa_squid 
| rare limit=3 cs_mime_type
```

![image](https://github.com/user-attachments/assets/a7b7178b-d8be-4230-87ee-6cd3f2b9ad37)

### Sales wants to know the 5 best-selling products for North American vendors over the previous week.

```bash
index=sales sourcetype=vendor_sales VendorID<4000 
| chart count by VendorCountry
```

![image](https://github.com/user-attachments/assets/f4a3dc0d-c839-4536-a543-e066d64a4708)

