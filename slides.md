---
theme: default
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
---

## Container Performance and Vulnerability Management for Container Security Using Docker Engine

Jaison Dennis 
<br/>
CS7A
<br/>
20CSA34

---
layout: default
---

# Contents

<Toc maxDepth="1"></Toc>

---
layout: default
---

# Introduction 

- Containers are lightweight virtualization that shares host kernel
- This leads to security issues like host access and limited isolation
- Docker is the most popular container technology
- Docker-sec secures containers by implementing access policies to limit capabilities


---
layout: default
---

![Figure 1](/intro1.png)
---
layout: default
---

# Background

- Containers vs virtual machines - architecture, performance, isolation
- Docker components - engine, client, daemon, containerd
- Container image creation and lifecycle management

---
layout: default
---

# Container vs Virtual Machines

- Overhead:
  - Containers have less overhead than virtual machines. 
  - Containers run through a shared kernel with the host computer, resulting in lower resource usage compared to VMs .
- Isolation:
  - Containers are considered to be more vulnerable to attacks.
  - Containers and hosts share the same kernel, malicious containers can potentially exploit the host kernel.

---
layout: default
---

# Container vs Virtual Machines

- Deployment Efficiency:
  - Containers can run on the same operating system, making the server more efficient and allowing for faster application deployment.
  - Multiple containers can be bundled into a single operating system, reducing complexity and dependencies .
- Security Concerns
  - Containers have been found to have security problems, including malicious container images and vulnerabilities in container applications.
  - Automated and standardized approaches are needed to implement security updates to Docker images .

---
layout: default
---

# Container vs Virtual Machines

- Performance: 
  - Docker containers, in particular, are described as having better performance and lower computational cost compared to virtual machines.
  - They offer advantages such as speed, portability, scalability, and rapid delivery.


---
layout: default
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
---

# Container Image Creation and Lifecycle Management

- Image Creation: 
  - Images are the building blocks of containers. 
Contains the necessary files, libraries, and configurations required to run an application. 
Images can be created manually or automatically using tools like Dockerfile, which specifies the steps to build an image. 
The process involves selecting a base image, adding dependencies, configuring the environment, and packaging the application code.

---
layout: default
---

# Container Image Creation and Lifecycle Management

- Image Versioning: 
  - Container images can have multiple versions to track changes and updates. Versioning allows for easy rollback to a previous version if issues arise.
  - It is important to maintain a versioning strategy and use appropriate tagging conventions to manage and track image versions effectively.

- Image Registry: 
  - Container images are stored in a registry, which acts as a cenralized repository. 
  - Registry allows users to push and pull images, making them accessible to different environments and users. 
  - Examples are Docker Hub, Google Container Registry, and Amazon Elastic Container Registry.

---
layout: default
---

# Container Image Creation and Lifecycle Management

- Image Distribution: 
  - Container images need to be distributed across different environments, such as development, testing, and production. 
  - This can be done manually or through automated processes like continuous integration and deployment pipelines. 
  - Proper image distribution ensures consistency and reproducibility across different environments.

- Image Security: 
  - Container images should be scanned for vulnerabilities and security issues before deployment. 
  - Vulnerability scanning tools can analyze the image and identify any known vulnerabilities in the software packages and libraries included in the image. 
  - Regular scanning and updating of images help mitigate security risks.

---
layout: default
---

# Container Image Creation and Lifecycle Management

- Image Lifecycle Management: 
  - Container images have a lifecycle that includes creation, distribution, deployment, and retirement. 
  - It is important to have a well-defined process for managing image lifecycles, including version control, image promotion, and image deprecation. 
  - This ensures that only trusted and up-to-date images are used in production environments.

---
layout: default
---
# Container Security Concerns

- Vulnerable images - dependencies, supply chain attacks
- Host kernel access - quickly escape isolation
- Resource sharing - processes, filesystem, network
- Limited isolation - namespaces, capabilities

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

---
layout: default
---

# Creating Container Profiles

- Extracts rules from config and expected usage
- Monitors container during training phase
- Limits capabilities to minimum required

---
layout: default
---

# Creating AppArmor Profiles 

- Docker-sec aims to create highly customized AppArmor profiles for each container to enhance container security . 
- Two main strategies: 
  - Static Analysis
  - Dynamic Testing.

---
layout: default
---

# Static Analysis

- Generate the initial Docker profiles. 
- Gathers valuable static information about the container and accesses its configuration. 
- Collects information such as the container name, version, package manager, description of the fundamental components, and known vulnerabilities associated with those components. 
- This information is used to construct the initial set of access rules for the container .

---
layout: default
---

# Dynamic Testing

- Improve the Docker profiles during container runtime.
- Monitors the container's behavior and extracting additional rules that further constrain the container's capabilities.
- Allows Docker-sec to represent the actual application behavior, file system, processes, and network isolation in the profiles. 
- By tracking the container's execution in real-time, Docker-sec can extract rules that provide more rigorous protection if needed .

---
layout: default
---

# Creating AppArmor Profiles 

- Combination of static analysis and dynamic testing enables Docker-sec to create highly customized AppArmor profiles for each container.
- The initial profiles are based on the container's settings, such as the mounted directories and files. 
- These profiles are then dynamically enhanced with rules extracted during the container's execution. 
- This approach ensures that the profiles accurately reflect the container's behavior and provide effective security measures .
- Docker-sec enhances container security by restricting the container's access to resources and minimizing the attack surface. 
- The profiles define the allowed accesses and enforce them, preventing unauthorized actions and reducing the risk of container-based attacks .

---
layout: default
---

# Building Secured RunC Profile

- RunC directly interacts with containers
- RunC
  - Lightweight, portable command-line tool that provides the runtime environment for containers. 
  - Open-source implementation of the Open Container Initiative (OCI) runtime specification . 
  - Responsible for creating and managing containers based on OCI-compliant container images.
- Locked down profile prevents host access
- Allows only essential capabilities

---
layout: default
---

# Securing Docker Daemon

- Daemon runs and manages containers
- Profile limits access to required services
- Prevents unauthorized changes

---
layout: default
---

# Process Isolation

- PID namespaces separate container processes
- Capabilities limit process interactions
- Prevents inter-container attacks

---
layout: default
---

# Filesystem Isolation

- Mount namespaces separate filesystem
- Remove capabilities to limit access
- Protects host filesystem from containers

---
layout: default
---

<img src="/intro4.png" alt="Figure 4" width="670" height="160" class="m-auto"/>

---
layout: default
---

# Network Isolation

- Network namespaces for separate stacks
- Limit connectivity between containers
- Prevents snooping and MITM attacks

---
layout: default
---

![Figure 5](/intro5.png)

---
layout: default
---

# Vulnerability Scanning

- Checks images against CVE databases
- Identifies flaws like SQLi, XSS, injections
- Addresses vulnerabilities proactively

---
layout: default
---

# Evaluation Methodology

- Compare secured vs unsecured containers
- Different workloads - CPU, memory, disk, network
- Measure performance overhead
<br/>
<img src="/intro3.png" alt="Figure 3" class="m-auto"/>

---
layout: default
---

# Performance Overhead

- Low overhead around 2-4% for container startup
- Minimal impact on application performance
- Acceptable cost for significantly improved security

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

---
layout: default
---

# Implementation

- Additional Docker client commands for security functions
- User interface provides visibility into profiles

---
layout: default
---

# Use Cases

- WordPress container deployment
- Arbitrary application containers
- Simulated attacks for validation

---
layout: default
---

# Conclusions

- Docker-sec constrains containers to only legitimate access
 -Low performance overhead around 2-4%
- Significantly enhances container security

---
layout: section
---

# Questions

---
layout: section
---

# Thank You