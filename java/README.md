# Ansible Role: java

安装JDK

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

	ansible `2.3.2.0`	
	os `Centos 7.2 X64`
	python `2.7.5`



## 依赖

没有


## Example Playbook
	
	jdk 1.7版本
    - hosts: node1
      roles:
        - java
		
	jdk 1.8版本
	- hosts: node1
	  roles:
	   - { role: java, java_version: "1.8" }

## 修改jdk版本步骤（先复制jdk.tar.gz到files，然后playbook中修改变量）
	
	jdk 1.8版本
	- hosts: node1
	  roles:
	   - { role: java, java_version: "1.8", java_home: "/usr/java/jdk1.8.0_1??", java_file: "jdk-8u1??-linux-x64.tar.gz", java_install_path: "{{ software_install_path }}/jdk1.8.0_1??"}
     
