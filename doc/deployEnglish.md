# 依赖准备

### 系统准备
- 系统安装盘下载链接: http://old-releases.ubuntu.com/releases/18.04.1/
- 系统安装链接: https://support.huawei.com/enterprise/zh/doc/EDOC1100136592/426cffd9

### 驱动准备
- 驱动下载链接：https://ascend.huawei.com/#/hardware/firmware-drivers
- 驱动安装链接：https://support.huaweicloud.com/instg-msInstall-cann202/atlasms_03_0002.html

# 镜像编译
### apulis镜像
- custom-user-dashboard-frontend  
  repo: https://github.com/apulis/user-dashboard-frontend  
  
- custom-user-dashboard-backend  
  repo: https://github.com/apulis/user-dashboard-backend  

- aiarts-frontend   
  repo: https://github.com/apulis/AIArts-Frontend  

- aiarts-backend   
  repo: https://github.com/apulis/AIArts-Backend  

- data-platform-backend  
  repo: 未开源   

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

### 第三方镜像
- grafana   
  repo: https://github.com/apulis/apulis_platform/tree/v1.5.0/src/docker-images/grafana  
  
- visualjob
  repo: https://github.com/apulis/DLWorkspace/tree/master/src/docker-images/visual-job 
  

# 服务部署
### 修改配置文件
 - hosts文件   
   文件路径：apulis-ytung-deploy/hosts   

   配置步骤   
   1、在 [kube-master] 下填写k8s集群的master节点（ip）  
   2、在 [kube-worker] 下填写k8s集群的worker节点（ip）。有多个worker节点时，直接换行填写即可。  
 - all.yaml文件  
   文件路径：apulis-ytung-deploy/group_vars/all.yaml  

   配置步骤   
   1、项目名称：PROJECT_NAME: "huawei"，这个名称将作为集群harbor保存镜像的项目名称   
   2、每个镜像的name和tag（包括基础镜像和服务镜像）。建议保持不变。  

 - cluster.yaml文件  
   文件路径：apulis-ytung-deploy/group_vars/all.yaml  
   
   配置步骤  
   1、kube vip地址：kubevipaddress: "192.168.3.9" （使用master的ip即可）

### 执行部署
 - ansible-playbook -i hosts 06.kube-init.yaml  
 - ansible-playbook -i hosts 08.network.yaml     
 - ansible-playbook -i hosts 09.storage.yaml  
 - ansible-playbook -i hosts 10.aiarts-service.yaml    

