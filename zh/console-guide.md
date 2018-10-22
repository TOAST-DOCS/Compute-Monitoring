## Compute > Monitoring > 控制台使用指南

## 主机监控

若想监控实例状态，需要先在 **Compute > Monitoring > Server Details**处添加相应实例之后才可进行实例的监控。

在**Server 名称**选择服务器，并点击 **添加** 按钮，即可监控实例详细信息。若不想再监控实例，则点击右侧 **删除** 按钮。在服务器详细信息中可监控的信息如下：

- Server 名称: 服务器名称
- IP: IP 地址
- vCPU: CPU 使用率
- 内存: 内存使用率
- 读取磁盘: 磁盘每秒读取的字节数
- 写入磁盘: 磁盘每秒写入的字节数
- 网络接收: 网卡每秒接收的字节数
- 网络发送: 网卡每秒发送的字节数
- 状态: 服务器状态
- 使用时间（耗时）: 服务器运行时间

若想查看服务器状态图表则选择**Graph** tap。

![[图 2 服务器状态图表]](http://static.toastoven.net/prod_infrastructure/monitoring/img_102.jpg)

按照搜索时间，显示于图表上的数据周期，将自动变更为 1分、 5分、 30分、 2小时。如果有不想再确认的图表，则点击 **删除** 按钮。

> [注意事项]  
> 监控数据的保存周期最多为一个月。并且图表时间也无法超过一个月。

## 报警日志

可在**Compute > Monitoring > Alarm Logs**确认alarm log列表。

可确认因超过用户定义的临界值而发送过报警的列表。如果想查看特定VM的报警列表，可以输入服务器名称或 IP 地址之后，再点击 **搜索** 按钮。

## 添加alarm

 在**Compute > Monitoring > Alarm Setting**点击 **添加**，可添加报警。

在**添加Alarm ** 窗口，添加要设置报警的服务器，再选定临界值和收信人。

### Server 名称选择

搜索并添加要设置报警的服务器。

### 设置临界值

设置将接收报警的实例系统资源及临界值。所支持的监控项中，包含有 CPU 使用率、内存使用量、磁盘使用量、网络使用量及服务器状态等。各监控项的说明及需要输入的临界值的信息如下：

|参数|	说明|
|---|---|
|CPU|	指CPU使用率。需要输入 0~100(%) 中的一个值。|
|内存|	指Memory 使用量。输入MB单位的绝对值。|
|Disk Read|	指磁盘读取使用量。对连接于实例的磁盘，输入以字节为单位的值。|
|Disk Write|	指磁盘写入使用量。对连接于实例的磁盘，输入以字节为单位的值。|
|Network In|	指所接收的网络流量。对连接于实例的以太网接口，输入以字节为单位的值。|
|Network Out|	指已发送的网络流量。对连接于实例的以太网接口，输入以字节为单位的值。|
|Server 停机|	指服务器的状态。所谓的服务器状态，判定与外部可进行通信的状态为正常。此Metric，无需输入额外的值。|

> [注意]  
> 若想使用**Server Down**，则应在实例中安装额外的 Monitoring 代理程序，同时该实例，应连接在与外部可进行通信的网络。

1. 在**Server 名称**中选择服务器，并点击 **添加** 按钮。 
2. 点击**+ 添加Alarm **。
3. **监控项** 列表中，选择要设置的监控项。
4. **临界值**中，选择条件后，再设定临界值。
5. 为了设置报警联系人，在 **收信人**中，点击**编辑** 按钮。
6. 如果出现**收信人**对话框，则添加项目成员。

### 设置收信人

选择将接收报警的项目成员，并选择接收报警的方法。

在**收信人** 输入框中，输入项目成员电子邮件，并点击 **添加** 按钮。

![[图6 Receiver设定]](http://static.toastoven.net/prod_infrastructure/monitoring/img_106.png)

## 修改及删除报警

在**Compute > Monitoring > Alarm Setting**中，可修改或删除报警。

如果想对报警进行更改，则点击列表中要进行修改的报警条目。与添加报警不同，一次只能修改一条报警。其余的，与添加报警相同。  
所添加的报警，可根据需要进行启用或停用。在列表中选择要启用或停用的报警之后，点击 **启用/停用** 按钮，则可对相关报警进行启用或停用处理。
不再需要使用某条警报时，可点击 **删除** 按钮删除相关报警。

## 设置监控代理程序

仅在使用Server Down Metric时，需要使用监控代理程序。

### 下载代理程序

[TOAST Downloads](https://docs.toast.com/en/Download/) 页面的 **Compute > Monitoring**中，下载 **Agent** 文件。

```
[root@host-192-168-0-7 ~]# wget http://static.toastoven.net/toastcloud/sdk_download/monitor/tcc/agent-centos-0.0.2.tgz
--2014-09-17 11:35:31--  http://static.toastoven.net/toastcloud/sdk_download/monitor/tcc/agent-centos-0.0.2.tgz
Connecting to http://static.toastoven.net... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168329 (164K) [application/x-gzip]
Saving to: “agent-centos-0.0.2.tgz”

100%[=======================================================>]
168,329     --.-K/s   in 0.005s

2014-09-17 11:35:31 (35.6 MB/s) - “agent-centos-0.0.2.tgz” saved [168329/168329]
```

### 安装代理程序

监控代理程序，必须通过root权限安装。如果想安装，则将已下载的文件解压之后执行'install.sh'即可。

```
[root@host-192-168-0-7 ~]# tar -zxvf agent-centos-0.0.2.tgz
./agent/
./agent/ssl/
./agent/ssl/cert.pem
./agent/ssl/.svn/
./agent/ssl/.svn/entries
./agent/ssl/.svn/text-base/
./agent/ssl/.svn/text-base/key.pem.svn-base
./agent/ssl/.svn/text-base/cert.pem.svn-base
./agent/ssl/.svn/tmp/
./agent/ssl/.svn/tmp/text-base/
./agent/ssl/.svn/tmp/prop-base/
./agent/ssl/.svn/tmp/props/
./agent/ssl/.svn/prop-base/
./agent/ssl/.svn/props/
./agent/ssl/.svn/all-wcprops
./agent/ssl/key.pem
./agent/conf.d/
./agent/conf.d/client.json
./agent/conf.d/rabbitmq.json
./agent/jq
./agent/sensu.repo
./agent/install.sh
./agent/plugins/
./agent/plugins/vm_checks_update.rb
./agent/plugins/VERSION
[root@host-192-168-0-7 ~]# cd agent
[root@host-192-168-0-7 ~]# sh install.sh
```

### 代理程序状态确认

输入'service sensu-client status'命令之后，若出现如下的'is running'，则表示运行正常。

```
[root@host-192-168-0-7 ~]# /etc/init.d/sensu-client status
sensu-client (pid 9223) is running...
```

非上述状态，则可利用'service sensu-client start'命令，并以手动方式启动。

```
[root@host-192-168-0-7 ~]# /etc/init.d/sensu-client start
Starting sensu-client [ OK ]
```
 一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一一 
一一一一
一一
一一


### 注意事项
监控代理程序，利用了开放源项目sensu。如果用户实例中已安装有其他sensu代理程序，则无法使用 TOAST监控代理程序。  
任意修改或删除/etc/sensu内的文件时，将会导致sensu不能正常工作。


