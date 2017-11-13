# Ansible Role: ambari server

只安装ambari server服务，不安装hadoop集群。

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

	ansible `2.3.2.0`
	os `Centos 7.2 X64`
	python `2.7.5`

## 角色变量

	software_files_path: "/opt/software"
	software_install_path: "/usr/local"
	ambari_http_path: "/var/www/html"
	ambari_version: "2.5.0.3"
	ambari_file: "ambari-{{ ambari_version }}-centos7.tar.gz"
	ambari_repo_path: "/etc/yum.repos.d/ambari.repo"

	HDP_version: "2.6.0.3"
	HDP_file: "HDP-{{ HDP_version }}-centos7-rpm.tar.gz"
	HDP_repo_path: "/etc/yum.repos.d/HDP.repo"

	HDP_UTILS_version: "1.1.0.21"
	HDP_UTILS_file: "HDP-UTILS-{{ HDP_UTILS_version }}-centos7.tar.gz"
	HDP_UTILS_path: "HDP-UTILS-{{ HDP_UTILS_version }}/repos/centos7"
	HDP_UTILS_repo_path: "/etc/yum.repos.d/HDP-UTILS.repo"

	jdbc_version: "5.1.40"
	jdbc_file: "mysql-connector-java-{{ jdbc_version }}.tar.gz"
	jdbc_file_path: "{{ software_files_path }}/{{ jdbc_file }}"
	jdbc_jar_file: "mysql-connector-java-{{ jdbc_version}}/mysql-connector-java-{{ jdbc_version }}-bin.jar"
	jdbc_file_url: "http://101.96.10.44/dev.mysql.com/get/Downloads/Connector-J/{{ jdbc_file }}"

	ambari_db_name: 'ambari'
	ambari_db_user: 'ambari'
	ambari_db_pass: 'ambari'

	hive_db_name: 'hive'
	hive_db_user: 'hive'
	hive_db_pass: 'hive'

	ambari_server_user: 'ambari'
	ambari_server_pass: 'ambari'
	ambari_server_database: 'mysql'
	mysql57_port: "3306"
	mysql57_user: "root"
	mysql57_password: "123456"
	java_home: '/usr/java/jdk1.8.0_144'
	remote_jar_path: "/usr/share/java"
	setup_statement_jdbc: 'ambari-server setup  --jdbc-driver={{ remote_jar_path }}/mysql-connector-java.jar --jdbc-db={{ ambari_server_database }} -v'
	setup_statement_database: 'ambari-server setup -j {{ java_home }} --databasehost={{ mysql_host }} --databasename={{ ambari_db_name }} --databaseusername={{ ambari_db_user }} --databasepassword={{ ambari_db_pass }} --databaseport={{ mysql57_port }} --database={{ ambari_server_database }} -v -s'
	ansible_python_interpreter: /usr/bin/python2.7

## 依赖
	java
	ambari-pre
	mysql57


## Example Playbook

    - hosts: ambari-server (仅server节点)
	  vars:
	   - mysql_host: 192.168.100.126
	   - mysql57_basedir: '/usr/local/mysql-5.7.20'
	  roles: 
           - { role: ambari-server , ambari_cluster_master: '192.168.100.126' }

## 使用

命令使用

```
# service ambari-server
 /usr/sbin/ambari-server {start|stop|reset|restart|upgrade|status|upgradestack|setup|setup-jce|setup-ldap|sync-ldap|set-current|setup-security|refresh-stack-hash|backup|restore|update-host-names|check-database|enable-stack|setup-sso|db-cleanup|install-mpack|uninstall-mpack|upgrade-mpack|setup-kerberos} [options]

```

web 使用

	http://ambari_cluster_master_ip:8080
	默认用户名/密码: admin/admin
	然后跟着web页面一步一步的部署hadoop集群
