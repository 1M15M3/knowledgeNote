# GitLab备份与恢复

---

* GitLab备份，默认会将文件备份到**/var/opt/gitlab/backups**目录

```shell
gitlab-rake gitlab:backup:create
```

* GitLab恢复，将文件拷贝到**/var/opt/gitlab/backups**目录下

```shell
gitlab-rake gitlab:backup:restore BACKUP=1393513186
```

### GitLab升级

* 查找GitLab软件包

```shell
rpm -qa
```

* 找到软件包**gitlab-ce-8.14.1-ce.1.el7.x86\_64**，版本可能不一样，然后进行卸载

```shell
rpm -e gitlab-ce-8.14.1-ce.1.el7.x86_64
```

* 安装新版

```shell
rpm -ivh gitlab-ce-8.17.4-ce.0.el7.x86_64.rpm
```

* 修改地址

```shell
vi /var/opt/gitlab/gitlab-rails/etc/gitlab.yml

host: git.chanpay.co
port: 443
https: true

gitlab-ctl stop
gitlab-ctl start
```

* 修改端口

```shell
vi /var/opt/gitlab/nginx/conf/gitlab-http.conf

listen *:9090;
```
