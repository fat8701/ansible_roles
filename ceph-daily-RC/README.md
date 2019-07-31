# Ansible Role: ceph-daily-RC

日常巡检操作

## 要求

此角色仅在Ubuntu及其衍生产品上运行。

## 测试环境

ansible `2.6.14`
os `Ubuntu 18.04`

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
    inspection_file: "/tmp/inspection.txt"  #输出文本
    wechat_scripts: "/tmp"   #脚本存放本地路径
    wechat_file: "wechat.py" #wechat告警脚本名
    #需要检查的域名
    check_domain:
            - http://xxxxxx.xxx.com
            - https://xxxxxx.xxx.com
            - http://xxx.xxx.xxx

## github地址

## Example Playbook
    - hosts: openstack
      any_errors_fatal: true
      roles:
       - role: ceph-daily-RC
      become: true
      become_user: root
      become_method: sudo
	   

