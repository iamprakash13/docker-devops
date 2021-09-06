# Running Airflow in docker
Airflow provides many plug-and-play operators that are ready to execute your tasks on Google Cloud Platform, Amazon Web Services, Microsoft Azure & other providers.
you can programtically author, schedule & manage your workflow using airflow UI.
It is one of the most robust platforms used by Data Engineers for orchestrating workflows or pipelines.

### Prerequisites:
- Install docker desktop on your windows https://docs.docker.com/desktop/windows/install/
- Install docker compose v1.27.0 or newer on your computer https://docs.docker.com/compose/install/
- if you're on windows os, install WSL from microsoft store or use virtualbox to run linux instance.
https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package


### Steps/commands:

1. Incase of windows use this cmd:
```
curl 'https://airflow.apache.org/docs/apache-airflow/2.1.3/docker-compose.yaml' -o docker-compose.yaml 
```
else:
```
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.1.3/docker-compose.yaml'
```

2. Intializing environment
Incase of windows use this cmd:
mkdir ./dags ./logs ./plugins
Set environment variable AIRFLOW_UID = 1000(id -u from WSL), AIRFLOW_GID = 0 in else: 
```
mkdir -p ./dags ./logs ./plugins
echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
```
docker-compose up airflow-init
By default, The account created has the login airflow and the password airflow

3. Running airflow
docker-compose up

4. Access airflow using browser
The webserver available at: http://localhost:8080
(OR)
by running commands:
docker-compose run airflow-worker airflow info


5. Cleaning up environment
docker-compose down --volumes --rmi all


---
> watch the video
<a href="http://www.youtube.com/watch?feature=player_embedded&v=rPv1wDQU6cw" target="_blank">
 <img src="http://img.youtube.com/vi/rPv1wDQU6cw/mqdefault.jpg" alt="Watch the video" width="240" height="180" border="10" />
</a>