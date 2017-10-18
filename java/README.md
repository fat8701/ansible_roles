# Ansible Role: java

添加jdk1.7版本

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
	   - { role: java ,java_version: "1.8" }
