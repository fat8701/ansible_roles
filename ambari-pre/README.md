# Ansible Role: ambari pre

安装ambari时需要做的预处理操作.

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

  ansible `2.3.2.0`
  os `Centos 7.2 X64`
  python `2.7.5`

## 角色变量

software_files_path: "/opt/software"
software_install_path: "/usr/local"

jdbc_version: "5.1.40"
jdbc_file: "mysql-connector-java-{{ jdbc_version }}.tar.gz"
jdbc_file_path: "{{ software_files_path }}/{{ jdbc_file }}"
jdbc_jar_file: "mysql-connector-java-{{ jdbc_version}}/mysql-connector-java-{{ jdbc_version }}-bin.jar"
jdbc_file_url: "http://dev.mysql.com/get/Downloads/Connector-J/{{ jdbc_file }}"
remote_jar_path: "/usr/share/java"

ansible_python_interpreter: /usr/bin/python2.7

## 依赖

没有


## Example Playbook

- hosts: ambari-all
  vars:
   - ipnames:
      '192.168.100.126': 'master.ambari.test'
      '192.168.100.127': 'slave-127.ambari.test'
      '192.168.100.128': 'slave-128.ambari.test'
  roles:
   - { role: ambari-pre , ambari_cluster_master: '192.168.100.126' }

