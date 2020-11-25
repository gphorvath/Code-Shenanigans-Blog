---
layout: post  
title: Setting Up Dev Environment
author: Gregory Horvath   
date: 2020-11-23
tags: blog Explanation 
---

# Intro
This is the first post in a series about setting up and experimenting with various Machine Learning tools.

# Setting up Development Environment
To begin, I am going to give a little insight into my dev environment to help others following this work. My dev environment is as follows:
* Windows 10 Version 2004 Build 19041 (Version 1903, Build 18362 or higher required for WSL2)
* Windows Subsystem for Linux 2 (WSL2) running Ubuntu 20.04 LTS
* Docker Desktop running WSL2 engine
* VS Code using Docker plugin

## Windows Subsystem for Linux 2 (WSL2) and Docker Desktop
1. To validate your version of Windows 10
    * Press WindowsKey-R  
    * Type "winver"
    * Press Enter
    * Version 1903, Build 18362 or higher required for WSL2
2. There are plenty of guides for installing WSL2, here is the one that worked for me: [How to Install WSL2 on Windows 10, Updated 10/30/2020](https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10)
3. In order to get Docker Desktop working properly with WSL2 I worked through a little trial/error with different posts I found.






The hardest part of setting this up was getting Docker running with WSL2. To help I used this [blog post](https://medium.com/@XanderGrzy/docker-in-windows-wsl-2-bc62b5236d1c).

Within (Admin) Powershell run the following:
```
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform

wsl --set-version Ubuntu 2
```

## VS Code and Extensions
The first step is to install VS Code on your host OS (Windows 10), not WSL2. The most recent version can be obtained here: https://code.visualstudio.com/.

Once installed, use the "Extension Market Place" to install the following extension, "Remote - WSL". Once you have done this, close VS Code and open WSL2. Once in WSL2, navigate to a directory where you intend to have your project and simply type:

``` bash
code .
```

This will open VS Code at this location within WSL. Now you can proceed to install any other extensions that you might find useful to your WSL2 remote host. To do this, search for the extension in the market place and click "Install on WSL: Ubuntu". Here is the list of extensions I found helpful for this project:
* Docker
* Python
* Python Auto Venv
* Code Spell Checker
* Jupyter
* Markdown All in One
* Jekyll Run (only used for creating/maintaining this blog)



# ML Flow
This document is intended to be a quick-start for those looking to gain familiarity with MLFlow. There are several design decisions (i.e. using environment variables to store keys) that are not conducive to production systems.[^blah]




## Setting up Tracking Server
This section is largely based off ML Flow Documentation as well as this blog post: [Deploy MLFlow with Docker Compose](https://towardsdatascience.com/deploy-mlflow-with-docker-compose-8059f16b6039
).  To begin, we need to setup the following:
* ML Flow Tracking Server
    * NGINX Reverse Proxy
    * MLFlow Tracking Server UI
    * Tracking Server DB: MySQL
    * Shared Artifact Storage: AWS S3 Bucket

I made it a point of posting the Docker implementation of the ML Flow Tracking Server here: https://github.com/gphorvath/mlflow-server-docker. Be sure to follow the directions in the README to setup your environment variables.



# Remaining Work:
* Connect MLFlow to a Github repo project
* Kaggle Leaf Classification within MLFlow 
* Serve MLFlow Models with Docker containers
* Blog Post / Slides  
* (Optional) Kaggle Titanic Data/Problem
* Submit ticket to MLFlow Git and/or Stack Overflow
* Lucid Chart







# \<Delete This\> Backup Info \<Delete This\>

useful urls: 
* https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.get_artifact_uri

* https://github.com/amesar/mlflow-examples
* https://medium.com/spencerweekly/dont-use-anaconda-how-to-setup-a-decent-machine-learning-environment-a69b19c24918
* https://github.com/amesar/mlflow-examples
* https://github.com/mlflow/mlflow/issues/572
* https://www.adaltas.com/en/2020/03/23/mlflow-open-source-ml-platform-tutorial/
* http://www.inanzzz.com/index.php/post/6fa7/creating-a-ssh-and-sftp-server-with-docker-compose
* https://github.com/caelor/docker-sftp-server/blob/master/bin/setup_environment
* https://github.com/rapidsai/cloud-ml-examples
* https://medium.com/rapids-ai/managing-and-deploying-high-performance-machine-learning-models-on-gpus-with-rapids-and-mlflow-753b6fcaf75a
* https://github.com/mlflow/mlflow/issues/2677
* https://github.com/mlflow/mlflow/issues/1338
* https://github.com/gphorvath/flower_classifier_mlflow
* 

Setting up SFTP Server for Artifacts
* https://hub.docker.com/r/atmoz/sftp
* https://turreta.com/2020/02/29/docker-compose-yml-for-sftp-by-atmoz/

Setting up FTP Server for Artifacts
* https://github.com/stilliard/docker-pure-ftpd

Production ML Models:
* https://towardsdatascience.com/putting-ml-in-production-ii-logging-and-monitoring-algorithms-91f174044e4e

[^
]:
    This is a foot note