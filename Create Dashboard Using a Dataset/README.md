'host=SplunkSrv01 backupduration=* domain=* | stats max(backupduration) by domain | head 5'

![image](https://github.com/Nisha318/Splunk-Projects/assets/12909665/777b2c5f-338c-4a9c-bb1a-717db17a7bed)


<img src="https://github.com/Nisha318/Splunk-Projects/blob/main/Files/Splunk%20Dashboard%201.png">


## Create a Dashboard Prototype



'| makeresults count=12 | streamstats count  | eval _time=_time-(count*3600) | eval drip =(random () % 3) + 1 | eval espresso =(random () % 3) + 1 | ev'

![image](https://github.com/user-attachments/assets/7c3f7715-ff84-462d-bbac-ea94ffbdd8c9)


'| makeresults count=3 | streamstats count
| eval host = case(count=1, "www1", count=2, "www2", count=3, "www3", count=4, null())
| eval 406 = case(count=1, 25, count=2, 39, count=3, 31, count=4, null())
| eval 500 = case(count=1, 25, count=2, 39, count=3, 31, count=4, null())
| eval 503 = case(count=1, 25, count=2, 39, count=3, 31, count=4, null())
| table host, 406, 500, 503'

![image](https://github.com/user-attachments/assets/9b87d572-8948-4fc9-9c28-213ac46c546d)
