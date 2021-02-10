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
