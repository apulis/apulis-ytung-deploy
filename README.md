# Dependency Preparation

### System preparation
- System installation package download link: http://old-releases.ubuntu.com/releases/18.04.1/
- System installation link: https://support.huawei.com/enterprise/zh/doc/EDOC1100136592/426cffd9

### Driver preparation
- Driver download link：https://ascend.huawei.com/#/hardware/firmware-drivers
- Driver installation link：https://support.huaweicloud.com/instg-msInstall-cann202/atlasms_03_0002.html

# Mirror compilation
### apulis mirror
- custom-user-dashboard-frontend  
  repo: https://github.com/apulis/user-dashboard-frontend  
  
- custom-user-dashboard-backend  
  repo: https://github.com/apulis/user-dashboard-backend  

- aiarts-frontend   
  repo: https://github.com/apulis/AIArts-Frontend  

- aiarts-backend   
  repo: https://github.com/apulis/AIArts-Backend  

- data-platform-backend  
  repo: https://github.com/apulis/data-platform-backend  

- data-platform-frontend  
  repo: https://github.com/apulis/image-label-frontend  

- jobmanager2   
  repo: https://github.com/apulis/apulis_platform/tree/v1.5.0/src/ClusterBootstrap   
  build cmd: ./deploy.py docker build restfulapi2   

- kfserving  
  repo: https://apulis-gitlab.apulis.cn/apulis/DLWorkspace/-/tree/develop/src/docker-images/kfserving

- openresty   
  repo: https://github.com/apulis/apulis_platform/tree/v1.5.0/src/docker-images/openresty 

- init-container 
  repo: https://github.com/apulis/DLWorkspace/tree/master/src/docker-images/init-container

- a910-device-plugin   
  repo: https://github.com/apulis/ascend-device-plugin  

- volcanosh  
  repo: https://github.com/apulis/ascend-for-volcano  

### Third party Mirror
- grafana   
  repo: https://github.com/apulis/apulis_platform/tree/v1.5.0/src/docker-images/grafana  
  
- visualjob
  repo: https://github.com/apulis/DLWorkspace/tree/master/src/docker-images/visual-job 
  

# Service Deployment

### Setup Ansible tools
* install by apt
```
apt update
apt install software-properties-common
apt-add-repository --yes --update ppa:ansible/ansible
apt install ansible
```

* install by python pip
```
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple && \
pip config set install.trusted-host mirrors.aliyun.com
pip install --user ansible
```

After installation, then check ansible version by command ```ansbible --version```,  and make sure ```version >= 2.9.*```

### Configuration file modification
 - hosts file which named ```hosts``` in root path, and then modify by use enviroment:  
   1、enter ip address of k8s cluster's master node into [kube-master]  
   2、enter ip address of k8s cluster's worder node into [kube-worker]. If there are multiple nodes, enter each ip in a new line.  

 - all.yaml file  
   file path：group_vars/all.yaml   

   Configuration :  
   1、project name：PROJECT_NAME: "huawei"，this name will be used as a project name for cluster image name prefix   
   2、for all mirrors, modification of name or tag is not suggested.(including basic mirror and service mirror)  

 - cluster.yaml file  
   file path：group_vars/all.yaml  
   
   configuration:  
   1、kube vip path：```kube_vip_address: "192.168.3.9"``` （use master's ip address）   

### Execute command for deployment  
 - ansible-playbook -i hosts 06.kube-init.yaml
 - ansible-playbook -i hosts 08.network.yaml
 - ansible-playbook -i hosts 09.storage.yaml
 - ansible-playbook -i hosts 10.aiarts-service.yaml

