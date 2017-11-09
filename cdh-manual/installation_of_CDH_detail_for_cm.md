## Installation Path B
### Installation Using Cloudera manager Parcels or Packages
 - 해당 인스톨 과정은 achive.cloudera.com에서 다운받은 package를 이용하여 설치한다.
 - To automate installation은 다음의 두가지를 만족 해야 함
  - 동일한 ssh port로 모든 호스트에 접근 가능해야 함
  - 모든 호스트는 archive.cloudera.com or local repo에 필요한 인스톨파일을 접근할수 있어야 함

#### prerequisite
- cloudera manager가 사용하는 DB를 설치해야 한다.
```
 sudo apt-get install mysql-server
```
- cloudera.list file(cloudera manager list file)이 /etc/apt/sources.list 파일로 저장되어야 함 [링크](https://www.cloudera.com/documentation/enterprise/release-notes/topics/cm_vd.html)
```
curl -O https://archive.cloudera.com/cm5/ubuntu/trusty/amd64/cm/cloudera.list
sudo cp cloudera.list /etc/apt/sources.list.d/
sudo apt-get update
```
```bash
# In ubuntu 16.04
curl -O https://archive.cloudera.com/cm5/ubuntu/xenial/amd64/cm/cloudera.list
sudo cp cloudera.list /etc/apt/sources.list.d/
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 327574EE02A818DD
wget http://archive.cloudera.com/cdh5/ubuntu/xenial/amd64/cdh/dists/xenial-cdh5/InRelease
w3m http://archive.cloudera.com/cdh5/ubuntu/xenial/amd64/cdh/dists/xenial-cdh5/contrib/binary-amd64 | cat
```
> Trouble shooting
 - [GPG error](https://askubuntu.com/questions/20725/gpg-error-the-following-signatures-couldnt-be-verified-because-the-public-key)
 - [Week digest algorithm](https://community.cloudera.com/t5/CDH-Manual-Installation/CDH-on-ubuntu-16-04-xenial/td-p/45125)


#### Install Cloudera manager server software
 - install oracle JDK
 ```
 sudo apt-get install oracle-j2sdk1.7
 ```

 - install the cloudera manager server packages
 ```
 sudo apt-get install -y cloudera-manager-daemons cloudera-manager-server
 ```

 - install mysqldb [설정참고](https://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_mysql.html)
 ```
 # mysql db
 sudo apt-get install mysql-server
 # mysql JDBC Driver
 sudo apt-get install libmysql-java
 ```

 - configuring mysql
 ```
 # database 파일들의 백업을 원할 경우 위 [설정참조]링크를 참조하여 db 설정을 변경해 줘야 함
 mysql -u root -p
 mysql> create database amon DEFAULT CHARACTER SET utf8;
 mysql> create database rman DEFAULT CHARACTER SET utf8;
 mysql> create database nav DEFAULT CHARACTER SET utf8;
 mysql> create database cmf DEFAULT CHARACTER SET utf8;
 mysql> create database navms DEFAULT CHARACTER SET utf8;
 mysql> grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'amon';
 mysql> grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';
 mysql> grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'nav';
 mysql> grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'navms';
 mysql> grant all on cmf.* TO 'cmf'@'%' IDENTIFIED BY 'qwer!234';
 ```

 ```
 # db 정보 입력
 vi /etc/cloudera-scm-server/db.properties
 # contents
 com.cloudera.cmf.db.type=mysql
 com.cloudera.cmf.db.host=127.0.0.1:3306
 com.cloudera.cmf.db.name=cmf
 com.cloudera.cmf.db.user=cmf
 com.cloudera.cmf.db.password=pass
 com.cloudera.cmf.db.setupType=EXTERNAL
 ```
 > Trouble shooting
  - [password policy requirement](http://xinet.kr/?p=974)

#### Start the cloudera manager server
 - start cloudera manager server
 ```
 systemctl start cloudera-scm-server
 ```
 > Trouble shooting
  - [cannot find repo](https://community.cloudera.com/t5/CDH-Manual-Installation/CDH-on-ubuntu-16-04-xenial/td-p/45125)

#### Connect Cloudera manager
 - connect http://cm_host:7180 (init account : admin, password : admin)  
 ![cm](./installation_of_CDH_detail_for_cm_img/cm_main_img.png)
 > Trouble shooting
  - [cloudera-manager troubleshooting](https://www.cloudera.com/documentation/enterprise/5-12-x/topics/cm_ig_troubleshooting.html#cmig_topic_19)
