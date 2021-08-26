---
layout: default
title: My experiences with Docker documentation
permalink: /my-experiences-with-Docker-doc/
---

# My experiences with Docker documentation
## Suggestions and queries to SMEs
### Reference Page: [Install Docker Desktop on Windows](https://docs.docker.com/desktop/windows/install/)

#### Suggestion

This suggestion is in reference to the instructions shared in the email to install WSL. Go to the exercise section in the email, see *Step 1: Install Docker Desktop on Windows*.

- Here, the quick instruction is to run the command `dism.exe` but it does not mention the entire command.
- Also, it does not specify that user needs to run PowerShell in Administrator mode.

*Suggestion:* 

To install WSL, the instructions must include that user needs to run the following command in PowerShell considering PowerShell is being run as Administrator,

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

>Refer to the detailed instructions available in [Microsoft suggested manual installation steps](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps).


> Another important consideration in such scenarios where the content is owned by third party (here, Microsoft WSL team) is to redirect users to the third party's website (that is, [Microsoft’s documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-1---enable-the-windows-subsystem-for-linux)). This will ensure that users refer to the latest content published by Microsoft.


#### Suggestion

This point is also in reference to the instruction of enabling the virtual machine feature as shared in the email.


To enable the virtual machine feature, we should instruct the user to run the entire command as mentioned below or redirect the user to [Microsoft’s documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-3---enable-virtual-machine-feature),

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Also, we must mention that PowerShell must be run in Administrator mode.

#### Question to SMEs

The instruction mentioned in the email says “No need to install a Linux distribution”. However, in Step 6 of the **Manual Installation Steps** to install WSL (in [Microsoft doc](https://docs.microsoft.com/en-us/windows/wsl/install-win10)), it is recommended to install at least one distribution. Same information is available in [Docker site](https://docs.docker.com/desktop/windows/install/) too.

*Question:*

Can we utilize Docker Desktop or run a simple app on a Docker container without installing any Linux distribution? What would be the impact in terms of technical aspect?

> I have high level understanding on this subject; so further research may be required.

#### Question to SMEs

Go to [Docker](https://docs.docker.com/desktop/windows/install/#whats-included-in-the-installer) website. Refer the following section(s),
> Containers and images created with Docker Desktop are shared between all user accounts on machines where it is installed. This is because all Windows accounts use the same VM to build and run containers. Note that it is not possible to share containers and images between user accounts when using the Docker Desktop WSL 2 backend.

*Question:*


- Does this mean that all containers and images are shared between all Windows accounts when we use WSL 1?
- If Yes, the content is incomplete and will need correction.


#### Suggestion

Go to [Docker](https://docs.docker.com/desktop/windows/install/#whats-included-in-the-installer) website. Refer the following section(s),

> Containers and images created with Docker Desktop are shared between all user accounts on machines where it is installed. This is because all Windows accounts use the same VM to build and run containers. Note that it is not possible to share containers and images between user accounts when using the Docker Desktop WSL 2 backend. Nested virtualization scenarios, such as running Docker Desktop on a VMWare or Parallels instance might work, but there are no guarantees. For more information, see Running Docker Desktop in nested virtualization scenarios.




*Suggestion:*

These information should be part of **Note** section for easy identification by users.

#### Suggestion

Go to [Docker](https://docs.docker.com/desktop/windows/install/#install-docker-desktop-on-windows) website. Refer the following section(s),
> 1. Double-click Docker Desktop Installer.exe to run the installer.

*Suggestion:*

As per MSTP guidelines, correct sentence construction should be,

To run the installer, double-click the **Docker Desktop Installer.exe**.


#### Suggestion

Go to [Docker](https://docs.docker.com/desktop/windows/install/#install-docker-desktop-on-windows) website. Refer the following section(s),
> 4. When the installation is successful, click Close to complete the installation process.

*Suggestion:*

Closing the Docker installation wizard and signing out are mandatory. So, updated content should be,

4. When the installation is successful, click **Close and sign out** to complete the installation process.

#### Suggestion

Go to [Docker](https://docs.docker.com/desktop/windows/install/#install-docker-desktop-on-windows) website. Refer the following step/section,
> 5. If your admin account is different to your user account, you must add the user to the docker-users group. Run Computer Management as an administrator and navigate to Local Users and Groups > Groups > docker-users. Right-click to add the user to the group. Log out and log back in for the changes to take effect.

*Suggestion:*

This step is crucial for users without having admin privileges. It must be part of an **Important** or **Note** section. Otherwise, this can be mentioned as the **Prerequisites**.

#### Suggestion

Refer the [page](https://docs.docker.com/desktop/windows/install/).

*Suggestion:*

Some language editing of content is required in the [page](https://docs.docker.com/desktop/windows/install/).

For example, in following section(s),
> Click Download update *When* you are ready to download the update. This downloads the update in the background. After downloading the update, click Update and restart from the Docker menu. This installs the latest update and restarts Docker Desktop for the changes to take effect.



### Reference Page: [Orientation and setup](https://docs.docker.com/get-started/)

#### Suggestion

Refer section [Start the tutorial](https://docs.docker.com/get-started/#start-the-tutorial)

*Suggestion:*

Need to add what we get after running the command. As a new user, it may be confusing to interpret the result after running the command `docker run -d -p 80:80 docker/getting-started`


### Reference Page: [Sample application](https://docs.docker.com/get-started/02_our_app/)

#### Suggestion

Refer the section [Get the app](https://docs.docker.com/get-started/02_our_app/#get-the-app) >> Step 1

*Suggestion:*

Need to add the reference to guide users to download an entire Git project in zipped format.

#### Suggestion

Refer the section [Build the app’s container image](https://docs.docker.com/get-started/02_our_app/#build-the-apps-container-image) >> Step 2

*Suggestion:*

The description given after the command `$  docker build -t getting-started .` must be displayed in tabular format by indicating what each parameter/ flag denotes.

For example,


|  Parameters/ Flags             |Available in? Dockerfile or Build command| Descriptions|
|----------------|-------------------------------|-----------------------------|
|node:12-alpine|Dockerfile            |   To instruct the builder that we want to start from the `node:12-alpine` image. But, since we didn’t have that on our machine, that image needed to be downloaded.         |
|yarn|Dockerfile                        |To install our application’s dependencies            |
|-t|Docker build command|To tag our image |







# Learnings
- Got the concept of WSL and how it can be installed on Windows machines post login.

- Learnt about containerization hands-on by running docker installation use cases. Also, I can relate containerization vis-a-vis virtualization and understand the differences to some extent.
- Learnt different terminologies used in Docker; for example, Docker Hub, Docker image and so on.
- Learnt about building the app’s [container image](https://docs.docker.com/get-started/02_our_app/#build-the-apps-container-image). Seems there are some similarities with configuring Ansible playbooks on which I had worked a few years back.
- Learnt the basics of building a container image and created a Dockerfile to do so.










