# Ansible Role: Fastdfs

安装Fastdfs

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible主机

    ansible: `2.3.2.0`
    os: `Centos 7.2 X64`
    python: `2.7.5`

ansible管理主机

    os: `Centos 6.7 X64   Centos 7.2 X64`
    
## 依赖

没有

## Example Playbook
	默认安装fastdfs

	- hosts: node1
	  roles:
	   - fastdfs


## 使用

```
/etc/init.d/nginx 
Usage: /etc/init.d/nginx {start|stop|reload|configtest|status|force-reload|upgrade|restart|reopen_logs}
/etc/init.d/fdfs_storaged
/etc/init.d/fdfs_storaged {start|stop|status|restart|condrestart}
/etc/init.d/fdfs_trackerd
/etc/init.d/fdfs_trackerd {start|stop|status|restart|condrestart}
```
