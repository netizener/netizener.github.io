---
layout: post
title:  "You don't need to struggle with Docker - builing a Node.js 'Hello World' Application with Docker "
date:   2020-12-01 
---
Docker is godsent! Want to seperate you developer environment from your main system? Dockerize it. Using bleeding edge technologies and don't want them to mess up with your system libraries? Dockerize it. Using Linux but want to use Android binaries on it? [Dockerize it](https://anbox.io/)

#### So what is Docker?
From the [official docs](https://docs.docker.com/get-started/overview/):
> Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.

#### How does Docker work?
Also from the [official docs](https://docs.docker.com/get-started/overview/):
> Docker provides the ability to package and run an application in a loosely isolated environment called a container....  Containers are lightweight because they don’t need the extra load of a hypervisor, but run directly within the host machine’s kernel. This means you can run more containers on a given hardware combination than if you were using virtual machines. 

` Enough introduction, let's get straight to the point!`
#### Working with Docker :
- ##### Setting up the developer environment & installing Docker:
    - For Windows 10 :
        > This guide is specific to Windows 10 versions 1903+. Use `winver` to check your Windows version, and ** UPDATE FIRST ** if necessary
        - Enable the Windows Subsystem for Linux 2 (Windows 10 v. 1903+) :
            - Open a Powershell window as an Administrator (using `Win + X` and selecting **Powershell (Admin)** option) and type :
                ```
                dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
                ```
            - Enable the Virtual Machine Feature using the Admin Powershell Window :
                ```
                dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
                ```
            - Download the [Linux Kernel Package for x64 machines](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) and install the downloaded package
            - Set WSL2 as the default version : 
                ```
                wsl --set-default-version 2
                ```
            - You're done setting up WSL2! For troubleshooting errors, refer to the [WSL Troubleshooting Page](https://docs.microsoft.com/en-us/windows/wsl/troubleshooting)
            - If everything till now happened smoothly, error-free, then [download Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows/) and install!
            - You will be asked to restart your PC. Save your work, and restart.
            - After your PC restarts, open up a command window and type : `docker run hello-world` to get a 'Hello World' from Docker! 
    - For Linux :
        > This guide is specific to Ubuntu. If you're using any other Ubuntu-based distributions, change `$(lsb_release -cs)` to your parent Ubuntu distribution. For other Linux distributions, follow the [official docs](https://docs.docker.com/engine/install/)
        - Open up a terminal, and paste the following lines :
            ```sh
            sudo apt-get remove docker docker-engine docker.io containerd runc
            sudo apt-get update
            sudo apt-get install git -y
            sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
            curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
            sudo apt-key fingerprint 0EBFCD88
            sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
            sudo apt-get update
            sudo apt-get install docker-ce docker-ce-cli containerd.io -y
            sudo groupadd docker
            sudo usermod -aG docker $USER
            ```
        - Before continuing further, save your work, and then restart using: ```sudo reboot```
        - After your PC restarts, open up a terminal and type : `docker run hello-world` to get a 'Hello World' from Docker! 
- ##### Building the Nodejs application:
    - Create a file called `app.js` and add the following lines of code :
        ```js
        var http = require('http');
        http.createServer(function (req, res) {
            res.write('Hello World!'); 
            res.end(); 
        }).listen(8080); 
        ```
        This creates a simple 'Hello World' application in Node.js using the inbuilt `http` module
    - Create a `Dockerfile` in the ***same*** directory and add the following lines of code :
        ```Dockerfile
        FROM node:12
        CMD ["node","app.js"]
        COPY app.js /app.js
        ```
    - Open a terminal and type the following lines to build the docker image:
        ```sh
        docker image build -t node-hello-world .
        ```
- ##### Testing the Nodejs application:
    - Open up a terminal and type : 
    ```sh
    docker run -p 8080:8080 -d node-hello-world
    ``` 
    - Fire up a browser and go to [localhost:8080](http://localhost:8080) to see our application in action!


**Congrats on building your Nodejs "Hello World" application using Docker!**
> Don't want to code? [Clone this repository](https://github.com/netizener/docker-node) and follow the instructions in the README!