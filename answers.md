Your answers to the questions go here.
##  Prerequisites - Setup the environment

Following instructions from Hiring exercise I set up  virtual environment with Vagrant on my computer. It was my first experience with vagrant so I use my time to learn about Vagrant from their introduction page on vagrantup.com. After that I opened Datadog account using “Datadog Recruiting Candidate” ( zoransasvic@me.com and Password: Application007). After signing up, I used plenty of time to familiarize myself with product before continuing with challenge.

## Collecting Metrics:


First task was to add  tags in the Agent config file. I used couple of tags for the purposes of the training such as app:frontend; app:intake; role:database; role:webserver. Screenshot was taken by accesing on Datadog website Infrastructure-HostMap and clicking on agents. Following the instructions I took a screenshot :

<img width="1237" alt="screen shot 2018-08-04 at 10 36 09 pm" src="https://user-images.githubusercontent.com/33996832/43683038-cfb1fdb6-9838-11e8-8559-be740ac3ac42.png">

## Database Integration

After initially struggling with Mongo; I decided to install PostgreSQL in the VE. Also I follow the examples how to integrate PostgreSQL on Datadog. Also Configuration file needed to be updated as well. Screenshot was taken by accessing DataDog website Dashboards-Dasboard List and clicking on Postgres-Metrics:

