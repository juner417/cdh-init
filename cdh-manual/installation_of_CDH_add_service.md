출처 : https://www.cloudera.com/documentation/enterprise/5-12-x/topics/cm_ig_install_path_b.html  
# Installation Using Cloudera manager with Parcels
- [installation_of_CDH_initialzing_node](installation_of_CDH_initializing_node.md)를 먼저 수행하고 진행해야 한다.
- 위 내용을 완료하면 cluster1이라는 이름의 클러스터가 생성된다.
- cluster1 drop button > Add Service를 클릭한 뒤 자신이 원하는 서비스를 선택한다(HDFS/YARN)
- CDH의 hadoop관련 모든 서비스는 **HDFS** 가 먼저 설치 되어야 한다(kafaka, zookeeper 및 client software 제외)  

## Add service(HDFS)

### Select the service to install   
 - HDFS 선택  
 ![hdfs_process0](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_00.PNG)

 > 주의!  
 > 각 서비스별 종속관계가 있으므로 미리 확인 후 선택해야 함  
 > CDH 5의 경우 YARN이 default이다.    
 > HDFS HA enable을 위해서는 zookeeper가 미리 설치되어야 한다.  

 - HDFS 기본 설정 구성  
 ![hdfs_process1](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_01.PNG)  
 ![hdfs_process2](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_02.PNG)

 - 설치  
 ![hdfs_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_03.PNG)  
 ![hdfs_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_05.PNG)  

 - 완료  
 ![hdfs_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_06.PNG)  
 > Tip!  
 > namenode, datanode 상세 설정이 필요한 경우 설치가 완료된 후에 설정 변경을 하면 된다.  
 > namenode HA를 위해서 zookeeper로 미리 설치하여야 한다.


 - HDFS master HA enable(HDFS > Actions > Enable High Availability)  
 ![hdfs_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_enableHA_01.PNG)  

 - namespace, secondary namenode, journalnode 지정  
 ![hdfs_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_enableHA_02.PNG)  

 - secondary namenode, journalnode 설정  
 ![hdfs_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_enableHA_03.PNG)  

 - 배포 및 시작  
 ![hdfs_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_enableHA_04.PNG)  

 - 완료  
 ![hdfs_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_HDFS_enableHA_05.PNG)  

 > Troubleshotting for installation of HDFS
  - [Troubleshotting](https://www.cloudera.com/documentation/enterprise/5-12-x/topics/cm_ig_troubleshooting.html)
  - [Configuring single user mode](https://www.cloudera.com/documentation/enterprise/latest/topics/install_singleuser_reqts.html)
  - [Permission Requirement](https://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_permissions.html)
  - [namenode format fail](https://community.cloudera.com/t5/Cloudera-Manager-Installation/Formatting-namenode-failed-java-io-IOException-Cannot-create/td-p/38354)


## Add service(YARN)

### Select the service to install
- YARN 선택  
![yarn_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_00.PNG)  
![yarn_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_01.PNG)  

> 주의!  
> 각 서비스별 종속관계가 있으므로 미리 확인 후 선택해야 함  
> CDH 5의 경우 YARN이 default이다.  

- YARN 기본 설정 구성  
![yarn_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_02.PNG)  
![yarn_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_03.PNG)  

- 설치  
![yarn_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_04.PNG)  

- 완료  
![yarn_process](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_05.PNG)  
> Tip!  
> resourcemanager, nodemanager 상세 설정이 필요한 경우 설치가 완료된 후에 설정 변경을 하면 된다.


- YARN master HA enable(YARN > Actions > Enable High Availability)  
![yarn_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_enableHA_01.PNG)  


- 배포 및 시작  
![yarn_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_enableHA_02.PNG)  

- 완료  
![yarn_ha](./installation_of_CDH_add_service_img/Choose_Cloudera_manager_edition_img_add_service_YARN_enableHA_03.PNG)  
