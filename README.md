[![kizito25](https://circleci.com/gh/Kizito25/project-ml-microservice-kubernetes/tree/main.svg?style=svg)](https://https://app.circleci.com/pipelines/github/Kizito25/project-ml-microservice-kubernetes)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

## Introduction of the project

project-ml-microservice-kubernetes is an Udacity project that configures, builds, lints and tests microservices in a containerized environment. 

## Motivation behind the project

There is a gap between development and deployment in a software development lifecycle. 
This project aims at testing my knowledge in eliminating these gaps that exist within the software development lifecycle.

## Tech Stack used in the project

Scripts in this project are written in Python and Bash.
There’s also Minikube for running a Kubernetes cluster, and Docker for containerization.


### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

##### Setup and Configure Docker locally
1. `sudo apt install apt-transport-https ca-certificates curl software-properties-common` 

2. `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

3. `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`  

4. `sudo apt update -y`

5. `apt-cache policy docker-ce`

6. `sudo apt install docker-ce`

7. `sudo systemctl status docker`

* Grant user permissions to docker executable

8. `sudo usermod -aG docker ${USER}`

9. `su - ${USER}`

10. `id -nG`

* Test docker
11. `docker ps`

##### Setup and Configure Kubernetes locally

* Minikube for Kubernetes - *For Linux*

1. `curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64`

2. `sudo install minikube-linux-amd64 /usr/local/bin/minikube`

3. `minikube version` - * to confirm if it installed successfully * 

4. `minikube start`

##### Create Flask app in Container

* Runing docker from the root directory builds the app in a docker container

1. `./run_docker.sh` - * create a docker image * 

2. `./upload_docker.sh` - * upload to docker repository.  you will need you docker login credentials for this* 

3. `.run_kubernetes.sh` - * Using Kubernetes to run a containerized deployment of our Flask App *

##### Run via kubectl`

* Install Kubectl

1. `curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"` - * download *

2. `sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl` - * install *

3. `kubectl version --client` - * Confirm Installation *
