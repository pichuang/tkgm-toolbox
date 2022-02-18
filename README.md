# Tanzu Kubernetes Grid Toolbox

> Speed delivery with Ansible and Tanzu Kubernetes Grid (TKGm)


```
                              \\\\\\\
                            \\\\\\\\\\\\
                          \\\\\\\\\\\\\\\
  -----------,-|           |C>   // )\\\\|
           ,','|          /    || ,'/////|
---------,','  |         (,    ||   /////
         ||    |          \\  ||||//''''|
VMware   ||    |           |||||||     _|
Tanzu    ||    |______      `````\____/ \
Kubernetes||    |     ,|         _/_____/ \
Grid     ||  ,'    ,' |        /          |
         ||,'    ,'   |       |  YOU    \  |
_________|/    ,'     |      /           | |
_____________,'      ,',_____|      |    | |
             |     ,','      |      |    | |
             |   ,','    ____|_____/    /  |
             | ,','  __/ |             /   |
_____________|','   ///_/-------------/   |
              |===========,'
```


## Current Environments
- VMware Tanzu Kubernetes Grid 1.4.1
- VMware vSphere 7.0.3 build: 19234570
- Bastion
    - 20.04.3 LTS (Focal Fossa)"
    - Ansible 2.9.6

## Toolbox
### Certificate
- [x] Add External Certificate - `ansible-playbook install-external-certs.yaml`

### Time
- [x] Check System Time - `ansible-playbook check-system-time.yaml`
- [ ] Config Time Service - `ansible-playbook check-system-time.yml`
