
# Windows

## Base Images

[Nano Server](https://hub.docker.com/_/microsoft-windows-nanoserver) : Built for .NET Core applications, is an ultralight Windows offering for new application development.

[Windows Server Core](https://hub.docker.com/_/microsoft-windows-servercore) : Supports traditional .NET framework applications, is medium in size and a good option for "lifting and shifting" Windows Server apps.

[Windows](https://hub.docker.com/_/microsoft-windows) : Provides the full Windows API set, is the largest image and has full Windows API support for workloads.

[Windows Server](https://hub.docker.com/_/microsoft-windows-server/) : Provides the full Windows API set, is slightly smaller than the Windows image, has full Windows API support, and allows you to use more server features.

## Guidelines on what image to use

Source: [Microsoft Article](https://learn.microsoft.com/en-us/virtualization/windowscontainers/manage-containers/container-base-images#guidelines)


- Are you building a Windows app based upon .NET Core? If the answer to this question is yes, you should target `Nanoserver`.

- Does your application require the full .NET framework? If the answer to this question is yes, you should target `Windows Server Core`.
  
- Is the Windows Server Core container image missing a dependency your app needs? If the answer to this question is yes, you should attempt to target `Windows`. This image is much larger than the other base images, but it carries many of the core Windows libraries (such as the GDI library).

- Do you need GPU acceleration support for your container workloads? If yes, you should consider using the `Windows Server` image to include hardware acceleration for your Windows containers workloads.

# Prequisites:
Reference: [prerequisites.md](../prerequisites.md)

# OCP 4.14 or older, Limitations:

[OpenShift Limitations](https://docs.openshift.com/container-platform/4.14/windows_containers/understanding-windows-container-workloads.html#windows-containers-release-notes-limitations_understanding-windows-container-workloads)

```
Image builds
OpenShift Pipelines
OpenShift Service Mesh
OpenShift monitoring of user-defined projects
OpenShift Serverless
Horizontal Pod Autoscaling
Vertical Pod Autoscaling
```

## Production OS Support
- Windows Server 2019
- Windows Server 2022

[Windows Machine Config Operator architecture diagram](https://docs.openshift.com/container-platform/4.14/windows_containers/understanding-windows-container-workloads.html#windows-workload-management_understanding-windows-container-workloads)


## Other limitations:
```
- For development, you can use Windows 10/11 locally with docker, but Microsoft/Kubernetes/Red Hat only support "Windows Server" for production on Kubernetes/OpenShift. - https://learn.microsoft.com/en-us/virtualization/windowscontainers/manage-containers/hyperv-container

- Hyper-V is NOT supported on Kubernetes/OpenShift. Only Process Isolation is supported.

- Container image build should be same as worker node build. The hotfix minor revisions are NOT required to be the same, but highly recommended to match.

- Windows Pods need GMSA to join Active Directory Domain - https://learn.microsoft.com/en-us/azure/aks/hybrid/prepare-windows-nodes-gmsa

```