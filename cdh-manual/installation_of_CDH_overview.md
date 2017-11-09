출처 : https://www.cloudera.com/documentation/enterprise/5-12-x/topics/installation_installation.html

# Install cloudera manager and CDH

## cloudera manager deployment
### 다음의 sw를 설치해야 함(requirements)
 - oracle jdk
 - cloudera manager server and agent packages
 - supporting database software
 - cdh and managed service software


cloudera manager installation 방식은 [3가지](https://www.cloudera.com/documentation/enterprise/5-12-x/topics/installation_installation.html#concept_qpf_2d2_2p)가 있는데
production 환경에서는 아래의 내용이 좋다.

### production deployment(installation path B)
 - manually install and configure database(for cloudera manager and hive metastore)
 - oracle JDK and Cloudera manager server packages on server host
 - There are two option for install; manually install it yourself or use cloudera manager to automate installation
 - To automate installation은 다음의 두가지를 만족 해야 함
  - 동일한 ssh port로 모든 호스트에 접근 가능해야 함
  - 모든 호스트는 archive.cloudera.com or local repo에 필요한 인스톨파일을 접근할수 있어야 함


### cloudera manager installation phases
 - 다음은 cloudera manager(below cm) 및 cm deployment of CDH 설치 순서이다.
 - 모든 순서는 필수이지만 다양한 방법으로 수행가능함

#### phase
> phase1 : install JDK

 - use cloudera manager installer
 - manually install

> phase2 : setup database

 - use cloudera manager installer
 - mannyally install(os package or binary)

> phase3 : install cloudera manager server

 - path A : cloudera manager installer
 - path B : linux package install
 - path C : tar balls

> phase4 : install cloudera manager agent

 - path A : cloudera manager installation wizard
 - path B : linux package install
 - path C : tar balls

> phase5 : install CDH and managed service software

 - path A : cloudera manager installation wizard
 - path B : linux package install
 - path C : tar balls

> phase6 : create, configure and start CDH and managed service

 - path A : cloudera manager installation wizard
 - path B : cloudera manager installation wizard
 - path C : cloudera manager installation wizard


**현재 우리의 CDH 설치 환경은 path A의 방법으로 한다.**
** cloudera manager가 미리 설치 되어야 하고, 모든 노드는 ubuntu repository, archive.cloudera.com이 접근 가능해야 한다.**

### cloudera manager installation software
 - 원본 문서에 보면 다양한 방법이 있다.
 - 하지만 우리가 사용하는 방법은 *__Installation path B__* 에서 __parcels__ 를 이용한 설치이다.

### cloudera manager installation wizard
 - Discovery cluster hosts
 - Optionally install the oracle JDK
 - Optionally install CDH, managed service and cloudera manager agent on cluster hosts
 - Select services
 - Map service roles to hosts(각 host들 service role을 생성해서 맵핑)
 - Edit service configurations
 - Start services
* 만약 설치 중간에 취소하면 모든 프로세스는 rollback되고 설치 이전의 상태로 돌아감

## Installation Path B
### Installation Using Cloudera manager Parcels or Packages
 - 해당 인스톨 과정은 achive.cloudera.com에서 다운받은 package를 이용하여 설치한다.
 - To automate installation은 다음의 두가지를 만족 해야 함
  - 동일한 ssh port로 모든 호스트에 접근 가능해야 함
  - 모든 호스트는 archive.cloudera.com or local repo에 필요한 인스톨파일을 접근할수 있어야 함
