Your answers to the questions go here.
##  Prerequisites - Setup the environment

Following instructions from Hiring exercise I set up  virtual environment with Vagrant on my computer. It was my first experience with vagrant so I use my time to learn about Vagrant from their introduction page on vagrantup.com. After that I opened Datadog account using “Datadog Recruiting Candidate” ( zoransasvic@me.com and Password: Application007). After signing up, I used plenty of time to familiarize myself with product before continuing with challenge.

## Collecting Metrics:


First task was to add  tags in the Agent config file. I used couple of tags for the purposes of the training such as app:frontend; app:intake; role:database; role:webserver. Screenshot was taken by accesing on Datadog website Infrastructure-HostMap and clicking on agents. Following the instructions I took a screenshot :

<img width="1237" alt="screen shot 2018-08-04 at 10 36 09 pm" src="https://user-images.githubusercontent.com/33996832/43683038-cfb1fdb6-9838-11e8-8559-be740ac3ac42.png">

## Database Integration

After initially struggling with Mongo; I decided to install PostgreSQL in the VE. Also I follow the examples how to integrate PostgreSQL on Datadog. Also Configuration file needed to be updated as well. Screenshot was taken by accessing DataDog website Dashboards-Dasboard List and clicking on Postgres-Metrics:

<img width="1299" alt="screen shot 2018-08-04 at 11 02 22 pm" src="https://user-images.githubusercontent.com/33996832/43683181-38b112c8-983b-11e8-9ece-b8090931f08f.png">

## Creating a custom Agent check

Last part of collecting metrics was to submits a metric named my_metric with a random value between 0 and 1000 and also change your check's collection interval so that it only submits the metric once every 45 seconds. After I creating a new file in Python I capture of process and code in following screenshots:

<img width="711" alt="screen shot 2018-08-02 at 11 18 09 am" src="https://user-images.githubusercontent.com/33996832/43683234-7ce8802e-983c-11e8-8307-9ae8eb2407fc.png">


