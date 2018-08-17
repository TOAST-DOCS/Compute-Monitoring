## Compute > Monitoring > 概要

Infrastructure服务中，将以提供用户所创建的实例相关监控功能为主。
可查看实例硬件资源使用量，并通过给使用量设置临界值以及利用电子邮件或者SMS来接收并查看对特定情况的报警。

下述内容为TOAST监控系统的架构：

![[监控系统架构拓扑]](http://static.toastoven.net/toastcloud/static/common/img/cms_img/monitoring/img_1.jpg)

监控系统以OpenStack的Ceilometer为基础进行拓展。因为主要通过管理程序，获得用户所创建实例资源使用量的相关信息，所以无需安装额外的监控程序。要想添加特殊监控项目(例：服务器停机与否) 则应在实例系统安装监控代理程序。

