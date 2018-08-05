Your answers to the questions go here.
##  Prerequisites - Setup the environment

Following instructions from Hiring exercise I set up  virtual environment with Vagrant on my computer. It was my first experience with vagrant so I use my time to learn about Vagrant from their introduction page on vagrantup.com. After that I opened Datadog account using “Datadog Recruiting Candidate” ( username:zoransasvic@me.com ). After signing up, I used plenty of time to familiarize myself with product before continuing with challenge.

## Collecting Metrics:


First task was to add  tags in the Agent config file. I used couple of tags for the purposes of the training such as app:frontend; app:intake; role:database; role:webserver. Screenshot was taken by accesing on Datadog website Infrastructure-HostMap and clicking on agents. Following the instructions I took a screenshot :

<img width="1237" alt="screen shot 2018-08-04 at 10 36 09 pm" src="https://user-images.githubusercontent.com/33996832/43683038-cfb1fdb6-9838-11e8-8559-be740ac3ac42.png">

## Database Integration

After initially struggling with Mongo; I decided to install PostgreSQL in the VE. Also I follow the examples how to integrate PostgreSQL on Datadog. Also Configuration file needed to be updated as well. Screenshot was taken by accessing DataDog website Dashboards-Dasboard List and clicking on Postgres-Metrics:

<img width="1299" alt="screen shot 2018-08-04 at 11 02 22 pm" src="https://user-images.githubusercontent.com/33996832/43683181-38b112c8-983b-11e8-9ece-b8090931f08f.png">

## Creating a custom Agent check

Last part of collecting metrics was to submits a metric named my_metric with a random value between 0 and 1000 and also change your check's collection interval so that it only submits the metric once every 45 seconds. After I creating a new file in Python I capture of process and code in following screenshots:

<img width="711" alt="screen shot 2018-08-02 at 11 18 09 am" src="https://user-images.githubusercontent.com/33996832/43683234-7ce8802e-983c-11e8-8307-9ae8eb2407fc.png">

<img width="492" alt="screen shot 2018-08-02 at 11 29 10 am" src="https://user-images.githubusercontent.com/33996832/43683248-909bf452-983c-11e8-8aa4-1a9d59d39a72.png">

<img width="518" alt="screen shot 2018-08-02 at 11 28 26 am" src="https://user-images.githubusercontent.com/33996832/43683256-a60e8fa2-983c-11e8-9041-845d1c17f2b7.png">

## Bonus Question

Bonus question was "Can you change the collection interval without modifying the Python check file you created"? , and answer is yes simply by using the User Interface from dataDog website. In order for you to do that click simply on Metrics -Summary and find file you want to modify. Cliuck on that file and click on a pennext to Metadata. After yopu modify changes you want, simply save changes. Screenshot of the process :

<img width="1395" alt="screen shot 2018-08-04 at 11 22 44 pm" src="https://user-images.githubusercontent.com/33996832/43683320-d90ff7f0-983d-11e8-882f-103bdb1b44fc.png">

## Visualizing Data: Timeboard

Part of this challenge was to utilize the Datadog API to create a Timeboard that contains: Your custom metric scoped over your host; any metric from the Integration on your Database with the anomaly function applied and your custom metric with the rollup function applied to sum up all the points for the past hour into one bucket. Timeboard with a name "Zoran-DataDog-Challenge:" was created and anomaly fucntion was applied as well as rollup function to sum up all points. Code is listed bellow:

```python
Last login: Sat Aug  4 19:44:22 on ttys002
➜  deploy cd ../
➜  Datadog-challenge ls
README.md                                deploy                                   ubuntu-xenial-16.04-cloudimg-console.log
app.py                                   hello.py
➜  Datadog-challenge vagrant ssh
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-131-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.


Last login: Sun Aug  5 08:22:21 2018 from 10.0.2.2
vagrant@ubuntu-xenial:~$ wget - 0 - http://0.0.0.0:8000
--2018-08-05 08:32:23--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:32:23--  http://0/
Resolving 0 (0)... 0.0.0.0
Connecting to 0 (0)|0.0.0.0|:80... failed: Connection refused.
--2018-08-05 08:32:23--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:32:23--  http://0.0.0.0:8000/
Connecting to 0.0.0.0:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29 [text/html]
Saving to: ‘index.html.6’

index.html.6                             100%[==================================================================================>]      29  --.-KB/s    in 0s      

2018-08-05 08:32:23 (5.71 MB/s) - ‘index.html.6’ saved [29/29]

FINISHED --2018-08-05 08:32:23--
Total wall clock time: 0.1s
Downloaded: 1 files, 29 in 0s (5.71 MB/s)
vagrant@ubuntu-xenial:~$ wget - 0 - http://0.0.0.0/api/apm:8000
--2018-08-05 08:32:35--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:32:35--  http://0/
Resolving 0 (0)... 0.0.0.0
Connecting to 0 (0)|0.0.0.0|:80... failed: Connection refused.
--2018-08-05 08:32:35--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:32:35--  http://0.0.0.0/api/apm:8000
Connecting to 0.0.0.0:80... failed: Connection refused.
vagrant@ubuntu-xenial:~$ wget - 0 - http://0.0.0.0:8000/api/apm
--2018-08-05 08:32:52--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:32:52--  http://0/
Resolving 0 (0)... 0.0.0.0
Connecting to 0 (0)|0.0.0.0|:80... failed: Connection refused.
--2018-08-05 08:32:52--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:32:52--  http://0.0.0.0:8000/api/apm
Connecting to 0.0.0.0:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19 [text/html]
Saving to: ‘apm.1’

apm.1                                    100%[==================================================================================>]      19  --.-KB/s    in 0s      

2018-08-05 08:32:52 (2.04 MB/s) - ‘apm.1’ saved [19/19]

FINISHED --2018-08-05 08:32:52--
Total wall clock time: 0.1s
Downloaded: 1 files, 19 in 0s (2.04 MB/s)
vagrant@ubuntu-xenial:~$ wget - 0 - http://0.0.0.0:8000/api/trace
--2018-08-05 08:35:54--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:35:54--  http://0/
Resolving 0 (0)... 0.0.0.0
Connecting to 0 (0)|0.0.0.0|:80... failed: Connection refused.
--2018-08-05 08:35:54--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:35:54--  http://0.0.0.0:8000/api/trace
Connecting to 0.0.0.0:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14 [text/html]
Saving to: ‘trace.2’

trace.2                                  100%[==================================================================================>]      14  --.-KB/s    in 0s      

2018-08-05 08:35:54 (1.06 MB/s) - ‘trace.2’ saved [14/14]

FINISHED --2018-08-05 08:35:54--
Total wall clock time: 0.1s
Downloaded: 1 files, 14 in 0s (1.06 MB/s)
vagrant@ubuntu-xenial:~$ wget - 0 - http://0.0.0.0:8000/api/trace
--2018-08-05 08:35:57--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:35:57--  http://0/
Resolving 0 (0)... 0.0.0.0
Connecting to 0 (0)|0.0.0.0|:80... failed: Connection refused.
--2018-08-05 08:35:57--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:35:57--  http://0.0.0.0:8000/api/trace
Connecting to 0.0.0.0:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14 [text/html]
Saving to: ‘trace.3’

trace.3                                  100%[==================================================================================>]      14  --.-KB/s    in 0s      

2018-08-05 08:35:57 (1.67 MB/s) - ‘trace.3’ saved [14/14]

FINISHED --2018-08-05 08:35:57--
Total wall clock time: 0.09s
Downloaded: 1 files, 14 in 0s (1.67 MB/s)
vagrant@ubuntu-xenial:~$ wget - 0 - http://0.0.0.0:8000/api/trace
--2018-08-05 08:35:59--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:35:59--  http://0/
Resolving 0 (0)... 0.0.0.0
Connecting to 0 (0)|0.0.0.0|:80... failed: Connection refused.
--2018-08-05 08:35:59--  http://-/
Resolving - (-)... failed: Name or service not known.
wget: unable to resolve host address ‘-’
--2018-08-05 08:35:59--  http://0.0.0.0:8000/api/trace
Connecting to 0.0.0.0:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14 [text/html]
Saving to: ‘trace.4’

trace.4                                  100%[==================================================================================>]      14  --.-KB/s    in 0s      

2018-08-05 08:35:59 (1.81 MB/s) - ‘trace.4’ saved [14/14]

FINISHED --2018-08-05 08:35:59--
Total wall clock time: 0.09s
Downloaded: 1 files, 14 in 0s (1.81 MB/s)
vagrant@ubuntu-xenial:~$ ls
apm    apm.py  app.pyc              index.html    index.html.2  index.html.4  index.html.6  trace    trace.2  trace.4
apm.1  app.py  ddagent-install.log  index.html.1  index.html.3  index.html.5  timeboard.py  trace.1  trace.3
vagrant@ubuntu-xenial:~$ rm index.html index.html.2 index.html.4
vagrant@ubuntu-xenial:~$ ls
apm    apm.py  app.pyc              index.html.1  index.html.5  timeboard.py  trace.1  trace.3
apm.1  app.py  ddagent-install.log  index.html.3  index.html.6  trace         trace.2  trace.4
vagrant@ubuntu-xenial:~$ rm index.html.1 index.html.5 index.html.3 index.html.6
vagrant@ubuntu-xenial:~$ ls
apm  apm.1  apm.py  app.py  app.pyc  ddagent-install.log  timeboard.py  trace  trace.1  trace.2  trace.3  trace.4
vagrant@ubuntu-xenial:~$ rm trace.1 trace.2 trace.3 trace.4
vagrant@ubuntu-xenial:~$ cd /etc/datadog-agent/
vagrant@ubuntu-xenial:/etc/datadog-agent$ ls
auth_token  checks.d  conf.d  datadog.yaml  datadog.yaml.example
vagrant@ubuntu-xenial:/etc/datadog-agent$ cd checks.d/
vagrant@ubuntu-xenial:/etc/datadog-agent/checks.d$ ls
checkvalue.py  checkvalue.pyc
vagrant@ubuntu-xenial:/etc/datadog-agent/checks.d$ cd /home/vagrant/
vagrant@ubuntu-xenial:~$ ls
apm  apm.1  apm.py  app.py  app.pyc  ddagent-install.log  timeboard.py  trace
vagrant@ubuntu-xenial:~$ vim timeboard.py 
vagrant@ubuntu-xenial:~$ python timeboard.py 
vagrant@ubuntu-xenial:~$ sudo service datadog-agent restart
vagrant@ubuntu-xenial:~$ vim timeboard.py 
vagrant@ubuntu-xenial:~$ touch timeboard2.py
vagrant@ubuntu-xenial:~$ vim timeboard2.py 
vagrant@ubuntu-xenial:~$ sudo service datadog-agent restart
vagrant@ubuntu-xenial:~$ python timeboard2.py 
vagrant@ubuntu-xenial:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
vagrant@ubuntu-xenial:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 258
Server version: 5.7.23-0ubuntu0.16.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases
    -> ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)

mysql> exit
Bye
vagrant@ubuntu-xenial:~$ vim timeboard2.py 

graphs = [
     {
        "definition": {
            "events": [],
            "requests": [
                {   "q": "avg:my_metric{host:ubuntu-xenial}",
                }
            ],
        },
        "title": "my_metric"
    },
     {
        "definition": {
            "events": [],
            "requests": [
                {
                    "q": "anomalies(avg:mysql.net.connections{host:ubuntu-xenial}, 'basic', 2)"
                }
            ],
        },
        "title": "mysql connections  anomalies"
    },
     {
        "definition": {
            "events": [],
            "requests": [
                {
                    "q": "avg:my_metric{host:ubuntu-xenial}.rollup(sum,3600)"
                }
            ],
        },
        "title": "my_metric rollup"
    },
]
read_only = True
api.Timeboard.create(title=title,
                     description=description,
                     graphs=graphs,
                     read_only=read_only)
                                                   
```

Screenshot of the timeBoard is privded here:




After accessing Dashboard from your Dashboard List in the UI, Timeboard's timeframe was set to the past 5 minutes. Snapshot of this graph was took and use the @ notation to send it to ourself .

<img width="503" alt="screen shot 2018-08-05 at 12 14 48 am" src="https://user-images.githubusercontent.com/33996832/43683651-314c5a2e-9845-11e8-9cc3-c27c205a1898.png">

## Bonus Question:

Bonus question was What is the Anomaly graph displaying? Anomaly detection is an algorithmic feature that allows you to identify when a metric is behaving differently than it has in the past, taking into account trends, seasonal day-of-week and time-of-day patterns. You can find more in DataDog docs on https://docs.datadoghq.com/monitors/monitor_types/anomaly/

## Monitoring Data

This part of the challenge was manipulation with the monitor. It was asked to create a new Metric Monitor that watches the average of your custom metric (my_metric) and will alert if it’s above the following values over the past 5 minutes:Warning threshold of 500;alerting threshold of 800 and also ensure that it will notify you if there is No Data for this query over the past 10m.Monitor’s message was created on the website under Monitor with warning/alerts and No data Info. 

```
{{#is_no_data}}data is missing in last 10 minutes. {{/is_no_data}}

{{#is_alert}}Alerting threshold of {{value}}, host ip address is {{host.ip}} {{/is_alert}}

{{#is_warning}} Warning threshold of {{value}}, host ip address is {{host.ip}} {{/is_warning}}

@zoransavic@me.com

```
This a screenshot of an e-mail that I recieved:

<img width="476" alt="screen shot 2018-08-05 at 12 48 52 am" src="https://user-images.githubusercontent.com/33996832/43683842-713a349a-9849-11e8-9024-ed6855d97d45.png">

## Bonus Question

Bonus question was to set up two scheduled downtimes for this monitor: One that silences it from 7pm to 9am daily on M-F and one that silences it all day on Sat-Sun.Also to set up an  email that  will notified when you schedule the downtime and take a screenshot of that notification.To do this you simply navigate on website to Monitors and choose Manage Downtime.There I set up two different downtimes. One that will run from Saturday 12:01 am until Sunday 11:59 pm and second that will be go daily from 7 pm until 9 am next day. I realized that two of them will run concurently over the weekend but that was necessary so downtime can be recurring. I alsno noticed that weekend one ending at Sunday midnight , when in reality it could be extended by Monday morning but that was already covered by Daily downtime (6 pm-9am). In the screenshot that I am submitting there is a typo that I fixed by editing the message.

<img width="508" alt="screen shot 2018-08-05 at 1 03 16 am" src="https://user-images.githubusercontent.com/33996832/43683955-5d709362-984b-11e8-9125-b939bf2e839d.png">

## Collecting APM Data:

In collecting APM Data I used FLASK APP that was provided :

```
from flask import Flask
import logging
import sys

from ddtrace import tracer
from ddtrace.contrib.flask import TraceMiddleware
from ddtrace import patch_all
import blinker as _

# Have flask use stdout as the logger
main_logger = logging.getLogger()
main_logger.setLevel(logging.DEBUG)
c = logging.StreamHandler(sys.stdout)
formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
c.setFormatter(formatter)
main_logger.addHandler(c)

app = Flask(__name__)

traced_app = TraceMiddleware(app, tracer, service="flask_trace", distributed_tracing=False)

@app.route('/')
def api_entry():
        return 'Entrypoint to the Application'
@app.route('/api/apm')
def apm_endpoint():
        return 'Getting APM Started'
@app.route('/api/trace')
def trace_endpoint():
        return 'Posting Traces'

if __name__ == '__main__':
        app.run(host='0.0.0.0', port='8000')
	
```
	
Screenshot is provided here:

<img width="669" alt="screen shot 2018-08-05 at 1 22 51 am" src="https://user-images.githubusercontent.com/33996832/43684083-66853284-984e-11e8-974b-516506acef37.png">

After that on DataDog website under the dashboard I added some of  APM data and system metric data.

<img width="1238" alt="screen shot 2018-08-05 at 1 38 05 am" src="https://user-images.githubusercontent.com/33996832/43684199-779429a2-9850-11e8-86ad-07f5442da6ad.png">

Public URL of that Dashobard Data is provided here: https://p.datadoghq.com/sb/2c0cfd46c-fc640196d77616c9c7f57554e53a6ef1



