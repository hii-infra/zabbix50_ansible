## 概要

Ansible用playbookです。
CentOS8環境に、Zabbix-server(rpm)とZabbix-agent(rpm)の機能を自動設定する。


## 対象環境

* CentOS8 ( RHEL8 )
* インターネットにつながり、ansibleサーバからrootユーザで直接sshできること

## 自動設定内容

* os(共通(common))
	+ selinux無効化
	+ zabbix-repoの登録

* zabbix-server
	+ zabbix5.0
	+ mariadb

* zabbix-agent
	+ zabbix-agent5.0

# 指定可能な設定内容

* zabbix50_ansible/roles/common/vars/main.yml

# ansible-playbook実行方法

zabbix50_ansibleフォルダに移動して、下記コマンドを実施

```
ansible-playbook -i zabbix50_ansible/inventory/inventory.ini zabbix50_ansible/site.yml
```

完了すると、zabbixサーバ上でzabbixサーバが稼働しています。以下、URLでアクセス可能。

```
http://{zabbix-ip}/zabbix
  ID = Admin
  PASS = zabbix
```
