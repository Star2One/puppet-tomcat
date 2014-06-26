
##Overview

安装Apache tomcat的puppet模块


##依赖

需要下载tomcat二进制安装包:

 * Tomcat 7:  <http://tomcat.apache.org/download-70.cgi>

仅支持 `*.tar.gz`格式安装包。
 
将安装包复制到files目录内。
  

##配置

##调用tomcat模块
将配置`include 'tomcat'`写到主配置文件`site.pp`内。

如下配置

方法1
    
```puppet
include tomcat
```
方法2

```puppet
class { '::tomcat':
  source        => 'apache-tomcat-7.0.39.tar.gz',
  deploymentdir => '/home/example.com/apps/apache-tomcat',
  user          => 'example.com',
  group         => 'mygroup',
  default_webapp_docs        => 'present',
  default_webapp_examples    => 'present',
  default_webapp_hostmanager => 'present',
  default_webapp_manager     => 'present',
  default_webapp_root        => 'present'
}
```


接下来，需要调用tomcat::install类。
配置如下

```puppet
tomcat::install { 'weittor.com-tomcat':
  source        => 'apache-tomcat-7.0.39.tar.gz',
  deploymentdir => '/home/example.com/apps/apache-tomcat',
  user          => 'example.com',
  group         => 'mygroup',
  default_webapp_docs        => 'present',
  default_webapp_examples    => 'present',
  default_webapp_hostmanager => 'present',
  default_webapp_manager     => 'present',
  default_webapp_root        => 'present'
}
```

##参数说明

`source`

源安装文件。
仅支持*.tar.gz*格式。

默认为: **apache-tomcat-7.0.50.tar.gz**

`deploymentdir`

安装目录。
默认为: **/opt/tomcat7**

`user`

用户名。
默认为: **tomcat**

`group`

用户组。
默认为: **tomcat**

`default_webapp_docs`

默认default_webapp_docs状态。   
可选参数；"present" or "absent"。

Default: **present**

`default_webapp_examples`

默认default_webapp_examples状态。          
可选参数："present" or "absent"。

Default: **present**

`default_webapp_hostmanager`

与上一个参数类似。

`default_webapp_manager`

与上一个参数类似。

`default_webapp_root`

与上一个参数类似。


#测试

系统版本： RHEL6\CentOS6             
Puppet版本：Puppet 3.4.x. on RHEL6

#Fork
翻译测试：www.weittor.com           
原作者：7terminals

