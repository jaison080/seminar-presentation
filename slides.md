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

- Cloud computing offers numerous advantages, including cost savings, scalability, and ease of storage.
- Containers have emerged as a simplified approach to virtualization, providing benefits over traditional virtual machines.
- Containers share the host kernel, resulting in lower overhead and simplified deployment.
- They are widely used in various applications, making cloud environments more efficient.

---
layout: default
level: 2
---

![Figure 1](/intro1.png)
---
layout: default
level: 2
---

# Addressing Container Security Challenges

- Containers are more vulnerable to attacks than virtual machines due to shared kernels.
- Security solutions like AppArmor and SELinux can enhance container security.
- Introducing Docker-sec, an automated security system with access policies and vulnerability scanning.
- The goal is to protect containers from attacks on both the server and container engine while minimizing performance impact.

---
layout: default
level: 2
---

# Managing Container Vulnerabilities

- Container vulnerabilities can arise from insecure libraries, dependencies, or malicious code.
- Scanning container images helps identify known vulnerabilities.
- Challenges include detecting undiscovered vulnerabilities and the limitations of image scanners.
- Container security involves addressing malicious container images and application vulnerabilities.

---
layout: default
---

# Related Work

- Introduction to studies and research on container security.
- Differentiating between static and dynamic schemes for vulnerability detection.
- Highlighting the relevance of real-life scenarios in assessing container security.
- Summarizing findings related to Docker's security and its popularity.

---
layout: default
level: 2
---

# Docker and Its Contribution to Network Security

- Discussing the impact of Docker on network security.
- Highlighting the benefits of Docker for edge computing.
- Analyzing the role of Docker in improving data center efficiency.
- Presenting studies on resource allocation for Docker-based applications.

---
layout: default
level: 2
---

# Continuous Security Assessment for Docker

- Introducing continuous security assessment in Docker development.
- Explaining the importance of verifying Docker image security.
- Presenting methods for dynamic analysis and security assessment.
- Highlighting the findings of research on Docker's security features and vulnerabilities.

---
layout: default
---

# Proposed Docker-Security Design

- Introduction to Docker as a leading container solution.
- The direct communication between containers and the host core.
- The importance of addressing security concerns.
- Reference to Docker-Sec for security solutions.
- Docker's security scanning for vulnerability detection.
<br/>
<br/>
<img src="/intro2.png" alt="Figure 2" class="m-auto"/>

---
layout: default
level: 2
---

<img src="/proposed.png" alt="Proposed System" width="470" height="120" class="m-auto"/>

---
layout: default
level: 2
---
# Isolation Mechanisms for Container Security

- Overview of Linux namespaces for container sandboxing.
- Explaining PID namespaces and their role in process isolation.
- Filesystem isolation and securing access to host file systems.
- Network isolation in Docker and its approach to protecting communication.
- The significance of Docker vulnerability scanning in enhancing security.

---
layout: default
level: 2
---

# Docker-Sec and Continuous Vulnerability Scanning

- Introduction to Docker-Sec and its role in security.
- Explanation of Docker profiles created for added protection.
- The process of Docker image scanning for vulnerabilities.
- Emphasizing the importance of continuous security assessment.
- The role of Docker-Sec in creating security profiles for containers.

---
layout: default
---

# Results

- Introduction to the performance assessment of Docker-Sec.
- Explanation of the assessment in two directions.
- Mention of workloads tested using primary operating system tools.
- Differentiation between secure Docker-sec and disabled containers.
- Performance time calculation and case scenarios.
<br/>
<img src="/intro3.png" alt="Figure 3" class="m-auto"/>
---
layout: default
level: 2
---

# Docker-Sec Overhead Assessment Results

- Overview of the assessment results for Docker-Sec's performance overhead.
- Discussion of overhead impact on CPU-bound applications.
- Analysis of performance tests and their impact on overhead.
- Comparison of overhead across different image types.
- Key findings from the performance assessment.

---
layout: default
level: 2
---

# Docker-Sec's Impact on Container Performance

- An overview of the impact of Docker-Sec on container performance.
- Discussion of how Docker-Sec imposes a relatively constant overhead.
- Explanation of factors affecting overhead, such as socket test duration.
- Importance of assessing performance across different Dockerfiles.
- Concluding remarks on Docker-Sec's performance impact.

---
layout: default
---

# Discussion

- Overview of the Docker-Sec framework.
- Description of its use of the Docker GUI with the -sec suffix.
- Mention of the use of AppArmor and a bash-wrapping efficiency.
- Key aspects of interaction with Docker-Sec, including creating containers and AppArmor profiles.
- Explanation of two scenarios covered in the demonstration section.

---
layout: default
level: 2
---

# Scenario 1 - Customized Security Profile

- Detailed explanation of the first scenario.
- Steps involved in creating a customized security profile for a specific container.
- Mention of launching a WordPress container with a profile generated by static testing.
- Description of dynamic control engine checks during the configuration.
- Discussion on how the dynamic profile interacts with the static profile during training.

---
layout: default
level: 2
---

<img src="/intro4.png" alt="Figure 4" width="670" height="160" class="m-auto"/>

---
layout: default
level: 2
---

# Scenario 2 - Benchmarking and Performance Testing

- Explanation of the second scenario.
- Details on running Docker-Sec for different Docker images with various capabilities.
- Association of generated profiles with containers using similar images.
- Discussion of performance benchmarks, including high application loads and computer stress loads.
- Importance of testing Docker-Sec in real-life and demanding situations.

---
layout: default
level: 2
---

![Figure 5](/intro5.png)

---
layout: default
level: 2
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

# Conclusion

- Overview of the advantages of container virtualization over hypervisor virtualization.
- Emphasis on the performance and security analysis of Docker, a popular container-based technology.
- Importance of vulnerability management in the context of containers and cloud-native technology.
- Mention of potential future tasks, such as comparing Docker container security with other technologies.
- Discussion on the improved stability and performance of Docker containers with modified default configurations.
- Summary of benchmark results indicating minimal overhead for a strain file system.

---
layout: section
---

# Thank You