# Ansible Role: startup-ceph-cluster

来电开机操作

## 要求

此角色仅在Ubuntu及其衍生产品上运行。

## 测试环境

ansible `2.6.14`
os `Ubuntu 16.04`

## 主机变量
     [ceph]
     ceph-test-1 ansible_host=xxx
     ceph-test-2 ansible_host=xxx

     [openstack]
     openstack-test ansible_host=xxx ansible_user="ubuntu" ansible_become_password="xxxxxx" 
     ceph-test-3 ansible_host=xxx

     [web:children]
     ceph
     openstack
	
## 系统变量
     mariadb_recovery_log: /root/mariadb_recovery.log

## github地址

## Example Playbook
     - hosts: openstack:web
       any_errors_fatal: true
       roles:
        - role: startup-ceph-cluster
       become: true
       become_user: root
       become_method: sudo
	   
