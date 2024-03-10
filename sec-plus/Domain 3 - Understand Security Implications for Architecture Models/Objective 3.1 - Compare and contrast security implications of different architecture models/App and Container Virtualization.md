---
tags:
topic: "sec_network_arch"
subTopic: "apps_containers"
source: "CompTIA"
family:  "sec_fundamentals"
imageNameKey: "SecPlus_apps_containers" 
cert: "Sec+"
---
# App and Container Virtualization
> *Creation Date:* `=this.file.cday`
> *Last Modified:* `=this.file.mday`

## Application Virtualization
- **Type**: A subset of Virtual Desktop Infrastructure (VDI).
- **Functionality**:
  - Allows access to applications hosted on a server.
  - Streams applications from the server to the client for local processing.
- **Solutions**:
  - **Citrix XenApp**: Formerly MetaFrame Presentation Server.
  - **Microsoft App-V**: Part of the Windows Server range.
  - **VMware ThinApp**: VMware's application virtualization product.
- **Usage with HTML5**: Often used with HTML5 remote desktop apps, enabling access through web browsers (clientless).

## Container Virtualization
- **Concept**: Dispenses with hypervisors and creates isolated environments at the OS level.
- **Implementation**:
  - OS defines isolated "cells" or containers for user instances.
  - Containers share the host OS kernel but have allocated CPU and memory resources.
  - Supports slightly different OS distributions but not entirely different OS types.
- **Application Process Containers**: Include necessary variables and libraries for specific applications.
- **Popular Product**: Docker (docker.com).
- **Applications in Cloud Services**:
  - Underpins microservices and serverless architectures.
  - Widely used for corporate workspaces on mobile devices.

## VMs vs. Containers
- **Virtual Machines (VMs)**:
  - Run entire OS instances on top of a hypervisor.
  - Each VM is fully isolated with its own OS.
- **Containers**:
  - Share the host OS kernel, lighter than VMs.
  - Run isolated applications with less overhead.

Containerization and application virtualization represent significant trends in IT architecture, offering different degrees of isolation, resource allocation, and scalability for various computing needs.

![[Knowledge-Base/Sec+/Domain 1 - General Security Concepts/Photos/SecPlus_apps_containers_1.png]]