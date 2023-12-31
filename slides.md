---
theme: bricks
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Container Performance and Vulnerability Management for Container Security Using Docker Engine
drawings:
  persist: false
transition: slide-left
title: Container Performance and Vulnerability Management for Container Security Using Docker Engine
mdc: true
layout: fact
---

## Container Performance and Vulnerability Management for Container Security Using Docker Engine

### Tahir Alyas , Sikandar Ali , Habib Ullah Khan , Ali Samad , Khalid Alissa , Muhammad Asif Saleem

Jaison Dennis 
<br/>
CS7A
<br/>
20CSA34

<!-- 
This presentation will provide an in-depth look at the research paper that proposes and evaluates a system called Docker-sec to enhance container security using the Docker engine.
 -->

---
layout: default
level: 2
---

# Contents

<Toc maxDepth="1"></Toc>

---
layout: default
---

# Introduction 

- Containers have much less overhead than virtual machines when they run through a kernel that they share with the host computer as user-space operations. 

- The device modules can also be used as lightweight units, and their delivery and execution are simplified. 
- It allows for the automatic control of large-scale systems .
- In short, everything involves building the container in whatever running environment, application, and all the libraries, triggers, and configuration files needed to run it.
- Since containers and hosts use the same kernel, malicious containers can quickly leave their environment and make host kernel attacks possible. 
- Mandatory kernel access control is the best way to improve the security of a Linux container by using tools such as AppArmor or SELinux to prevent unintended operations on both the host and container sides

---
layout: default
level: 2
---

# Docker Components

- Engine: 
  - Client-server program responsible for creating and running Docker containers. 
- Client :
  - Command-line interface (CLI) tool that allows users to interact with the Docker daemon and perform various operations related to Docker containers and images. 
- Daemon :  
  - Background process that runs on a host machine and is responsible for managing Docker containers.
  - Core component of the Docker Engine and handles the creation, execution, and monitoring of containers. 
- Containerd :
  - Open-Source container runtime that provides a platform-agnostic interface for managing container lifecycle operations, such as creating, running, and deleting containers.

---
layout: default
level: 2
---

![Figure 1](/intro1.png)

---
layout: default
level: 2
---

# Container Image Creation and Lifecycle Management

- Image Creation: 
  - Images are the building blocks of containers. 
  - Contains the necessary files, libraries, and configurations required to run an application. 
  - Images can be created manually or automatically using tools like Dockerfile, which specifies the steps to build an image. 
  - The process involves selecting a base image, adding dependencies, configuring the environment, and packaging the application code.

---
layout: default
level: 2
---

# Container Image Creation and Lifecycle Management

- Image Distribution: 
  - Container images need to be distributed across different environments, such as development, testing, and production. 
  - This can be done manually or through automated processes like continuous integration and deployment pipelines. 
  - Proper image distribution ensures consistency and reproducibility across different environments.

---
layout: default
level: 2
---

# Container Image Creation and Lifecycle Management

- Image Registry: 
  - Container images are stored in a registry, which acts as a cenralized repository. 
  - Registry allows users to push and pull images, making them accessible to different environments and users. 
  - Examples are Docker Hub, Google Container Registry, and Amazon Elastic Container Registry.

- Image Security: 
  - Container images should be scanned for vulnerabilities and security issues before deployment. 
  - Vulnerability scanning tools can analyze the image and identify any known vulnerabilities in the software packages and libraries included in the image. 
  - Regular scanning and updating of images help mitigate security risks.

---
layout: default
---
# Literature Survey

- <b>N. Tabassum, T. Alyas, M. Hamid, M. Saleem, S. Malik, and S. Binish Zahra, “Qos based cloud security evaluation using neuro fuzzy model,” </b>
  -  DIVA System 
  -  Analyzed 356,218 images : 
     -  Contain more than 180 errors on average, taking into account all models, 
     -  Many images have not been updated for hundreds of days 
- <b>M. Mohamed, R. Engel, A. Warke, S. Berman, and H. Ludwig, “Extensible persistence as a service for containers,” </b>
  - Explored the vulnerability-oriented of the Docker Environment
  - Explored safety consequences of using containers on traditional applications. 
  - Docker can help in all solutions for container security. 

<!--
DIVA System that automatically finds installations and parses public and group images in the Docker Hub
-->

---
layout: default
level: 2
---
# Literature Survey
 
- <b>F. D’Urso, C. Santoro, and F. F. Santoro, “Wale: a solution to share libraries in Docker containers,” </b>
  - Described the security issues of containers and the problems associated with containers being lightweight and using the same kernel as the Host operating system.
  - Presents four cases and solutions obtained. 
    - Securing the container from the applications inside it, 
    - Inter-container protection, 
    - Protecting the host from the containers
    - Securing the containers from a malicious or semi-honest host.

<!--
First, three use cases are handled by software, and the fourth is handled by hardware.
-->

---
layout: default
level: 2
---
# Literature Survey

- <b>S. Sultan, I. Ahmad, and T. Dimitriou, “Container security: issues, challenges, and the road ahead,”</b>
  - Described Docker and its performance analysis and took the stance that Docker has a protected layer on the container
  - Docker used a tool known as “Docker Engine” to execute the applications. 
  - Provided a Docker Hub for sharing applications it worked the same as virtual machines. 
  - Described the advantages of Docker containers over virtual machines.

<!--

-->

---
layout: default
---

# Proposed Docker-Sec System

- Implements mandatory access control policies
- Constraints containers based on expected usage
- Static analysis for initial rules, dynamic monitoring adds rules
<br/>
<br/>
<img src="/intro2.png" alt="Figure 2" class="m-auto"/>

<!--
Docker-sec implements mandatory access control policies to constrain containers based on the expected legitimate usage of the application. It conducts static analysis to generate an initial set of security rules. Further rules are added dynamically through runtime monitoring.
-->

---
layout: default
---

<img src="/proposed.png" alt="Proposed System" width="470" height="120" class="m-auto"/>


---
layout: default
---

# Docker-Sec Architecture

- Docker client, daemon, containerd runtime
- Static analyzer, dynamic monitor
- AppArmor profiles containers
- Vulnerability scanner checks images

<!--
Cover Docker-sec architecture including core Docker components like client, daemon, containerd. Highlight the static analyzer, dynamic monitor, AppArmor profiler which generates custom profiles for each container, and vulnerability scanner which checks container images.
-->

---
layout: default
level: 2
---

# Creating Container Profiles

- Extracts rules from config and expected usage
- Monitors container during training phase
- Limits capabilities to minimum required

<!--
Explain in depth how Docker-sec creates highly customized AppArmor profiles for each container. Rules are extracted from the container config and expected usage parameters. The container is monitored during a training period to build the profile. This allows limiting capabilities to the bare minimum required for operation.
-->

---
layout: default
level: 2
---

# Creating AppArmor Profiles 

- Docker-sec aims to create highly customized AppArmor profiles for each container to enhance container security . 
- Two main strategies: 
  - Static Analysis
  - Dynamic Testing.

---
layout: default
level: 2
---

# Static Analysis

- Generate the initial Docker profiles. 
- Gathers valuable static information about the container and accesses its configuration. 
- Collects information such as the container name, version, package manager, description of the fundamental components, and known vulnerabilities associated with those components. 
- This information is used to construct the initial set of access rules for the container .

---
layout: default
level: 2
---

# Dynamic Testing

- Improve the Docker profiles during container runtime.
- Monitors the container's behavior and extracting additional rules that further constrain the container's capabilities.
- Allows Docker-sec to represent the actual application behavior, file system, processes, and network isolation in the profiles. 
- By tracking the container's execution in real-time, Docker-sec can extract rules that provide more rigorous protection if needed .

---
layout: default
level: 2
---

# Building Secured RunC Profile

- RunC directly interacts with containers
- RunC
  - Lightweight, portable command-line tool that provides the runtime environment for containers. 
  - Open-source implementation of the Open Container Initiative (OCI) runtime specification . 
  - Responsible for creating and managing containers based on OCI-compliant container images.
- Locked down profile prevents host access
- Allows only essential capabilities

<!--
The RunC component interacts directly with containers at a low level. Docker-sec builds a locked down AppArmor profile for RunC, allowing only essential capabilities and preventing any host access through it.
-->

---
layout: default
level: 2
---

# Securing Docker Daemon

- Daemon runs and manages containers
- Profile limits access to required services
- Prevents unauthorized changes

<!--
Since the Docker daemon runs and manages all containers, its access is restricted through an AppArmor profile to only required services. This prevents any unauthorized changes through the daemon.
-->

---
layout: default
level: 2
---

# Process Isolation

- PID namespaces separate container processes
- Capabilities limit process interactions
- Prevents inter-container attacks

<!--
Docker-sec provides multi-layered process isolation using PID namespaces to separate container processes from host and other containers. Capabilities are restricted to limit inter-process interactions. This prevents inter-container attacks.
-->

---
layout: default
level: 2
---

# Filesystem Isolation

- Mount namespaces separate filesystem
- Remove capabilities to limit access
- Protects host filesystem from containers

<!--
For filesystem isolation Docker-sec uses mount namespaces to create separate filesystem views for each container. Capabilities that allow filesystem access are removed. Together this protects the host filesystem from being accessed or changed by a container.
-->

---
layout: default
level: 2
---

<img src="/intro4.png" alt="Figure 4" width="670" height="160" class="m-auto"/>

---
layout: default
level: 2
---

# Network Isolation

- Network namespaces for separate stacks
- Limit connectivity between containers
- Prevents snooping and MITM attacks

<!--
At the network level, Docker-sec uses network namespaces to create separate networking stacks for each container. Connectivity between containers is limited to only what is required. This prevents snooping or man-in-the-middle attacks between containers or from containers to the host.
-->

---
layout: default
level: 2
---

![Figure 5](/intro5.png)

---
layout: default
level: 2
---

# Vulnerability Scanning

- Checks images against CVE databases
- Identifies flaws like SQLi, XSS, injections
- Addresses vulnerabilities proactively

<!--
Docker-sec scans container images against CVE vulnerability databases to identify issues like SQL injection, XSS, unauthorized command execution before deployment. This allows vulnerabilities to be addressed proactively.
-->

---
layout: default
---

# Evaluation Methodology

- Compare secured vs unsecured containers
- Different workloads - CPU, memory, disk, network
- Measure performance overhead
<br/>
<img src="/intro3.png" alt="Figure 3" class="m-auto"/>

<!--
The researchers evaluated Docker-sec thoroughly by comparing secured containers protected by it versus unsecured containers across different workloads including CPU, memory, disk and network. They measured the performance overhead introduced by the security mechanisms.
-->

---
layout: default
level: 2
---

# Performance Overhead

- Low overhead around 2-4% for container startup
- Minimal impact on application performance
- Acceptable cost for significantly improved security

<!--
Docker-sec introduced low overhead of around 2-4% for container startup time. The impact on application performance after startup was found to be minimal. This is considered an acceptable cost for the significantly improved security provided by Docker-sec.
-->

---
layout: default
---

<div class="flex space-x-4">
  <div class="w-1/2">
    <img src="/intro6.png" alt="Figure 6" class="mx-auto" />
  </div>
  <div class="w-1/2">
    <img src="/intro7.png" alt="Figure 7" class="mx-auto" />
  </div>
</div>

---
layout: default
---

# Container Isolation

- Prevents inter-container attacks and limits host access
- Reduces attack surface through restricted capabilities

<!--
Summarize how Docker-sec provides multi-layered isolation between containers and from the host system.
AppArmor Profiles, Process Isolation, Filesystem Isolation, Network Isolation, Vulnerability Scanning
This reduces the attack surface significantly by restricting container capabilities.
-->

---
layout: default
---

# Use Cases

- WordPress container deployment
- Arbitrary application containers
- Simulated attacks for validation

<!--
The researchers validated Docker-sec on real-world use cases including deploying a WordPress container and running arbitrary application containers. They simulated attacks against these environments to validate the security.
-->

---
layout: default
---

# Conclusions

- Docker-sec constrains containers to only legitimate access
 -Low performance overhead around 2-4%
- Significantly enhances container security
- Additional Docker client commands for security functions
- User interface provides visibility into profiles

<!--
In conclusion, Docker-sec successfully constrained containers by limiting access to only legitimate needs required for proper functioning. It incurred low overhead of just 2-4% in testing. Overall it significantly improves the security of Docker containers.Docker-sec implements additional Docker client commands to activate its security functions like creating profiles. It also provides a user interface that gives visibility into the generated profiles.
-->

---
layout: quote
level: 2
---

# Questions

---
layout: statement
level: 2
---

# Thank You
