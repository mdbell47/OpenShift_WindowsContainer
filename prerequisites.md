## Prerequisites

### 1. Create RuntimeClass, recommended for easier reference
```
apiVersion: node.k8s.io/v1
kind: RuntimeClass
metadata:
  name: windows2022
handler: 'runhcs-wcow-process'
scheduling:
  nodeSelector: 
    kubernetes.io/os: 'windows'
    kubernetes.io/arch: 'amd64'
    node.kubernetes.io/windows-build: '10.0.20348' #This is for 2022, #2019 is: 10.0.17763
  tolerations: 
  - effect: NoSchedule
    key: os
    operator: Equal
    value: "windows"
  - effect: NoSchedule
    key: os
    operator: Equal
    value: "Windows"
```

### 2. Add trust certs to node for Image Pull
```
scp -i ~/.ssh/windows yourintermediate.crt capi@10.123.4.5:/C:/Users/capi/Documents
scp -i ~/.ssh/windows your-root.crt capi@10.123.4.5:/C:/Users/capi/Documents
ssh capi@10.123.4.5 -i ~/.ssh/windows

powershell
cd ~\Documents\
Import-Certificate -FilePath ".\yourintermediate.crt" -CertStoreLocation Cert:\LocalMachine\Root
Import-Certificate -FilePath ".\your-root.crt" -CertStoreLocation Cert:\LocalMachine\Root
```