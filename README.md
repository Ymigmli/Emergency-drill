# Emergency-drill
用于应急演练、技术分享或者内训

yjyl.tar.gz
  html.tar.gz  抵抗敏感词/敏感图片攻击环境
  xmr.tar.gz   抵抗操作系统恶意程序攻击
  yjyl.sh      如果都在centos 6环境下，一键部署，但xmr.tar.gz环境不会自启动
 
html.tar.gz
  使用方法
    放入到任意中间件即可，如果两个场景一起体现，则建议centos 6 ，该版本默认安装了httpd服务。
  功能
    演练直接显示敏感词，是否可以正常监测(后续敏感词在服务端已加密，客户端访问解密)
    演练抗CC攻击防护启用验证机制后是否可以正常监测
    演练只有对应省份的IP(例如IP归属地为湖北省)才能看到敏感词是否可以正常监测,火狐浏览器读不到returnCitySN导致无法触发
    演练只有从搜索引擎(例如google)获取到的链接才含有敏感词，直接访问无敏感词是否可以正常监测
    演练只有特定的浏览器访问才包含敏感词是否可以正常监测
    演练是否可以正常监测静/动态图片含有的敏感词和涩清内容
    工具：修改本地hosts文件，将www.google.cn解析到该站点IP使用域名进行访问，并点击后续页面的跳转，即可发现敏感词，在客户端http头部伪造插入Referer字段，服务器抓包 也能看到referer字段但并不会触发（已测试火狐浏览器）

xmr.tar.gz
  0x00 版本
    v1.0 2019.09 *
    v2.0 2019.12 去除挖矿程序，使用其他模拟挖矿网络/占用CPU资源的行为，防止发生风险和意外

  0x01 使用方法
		sh start.sh				一键部署环境
		unset LD_PRELOAD && sh delete.sh or sh delete.sh 2>/dev/null 一键删除环境
      delete.sh删除文件3后，LD_PRELOAD会因无法找到文件3导致当前shell命令执行报错,unset LD_PRELOAD无法在shell脚本中执行，两种方式都可实现删除环境不报错

  0x02 文件说明
    1           "挖矿"网络程序
    2           "挖矿"占用CPU程序
	  3           .so全局劫持文件
	  4           "挖矿"启动程序
	  delete.sh		删除"挖矿"环境脚本
	  history			复制已有history记录到该目录下
	  sourcefile		源文件夹
	  start.sh		部署"挖矿"环境脚本

  0x03 适用操作系统
    Centos6
    Centos7
    其他系统未测试

  0x04 by:捕影.竹林再遇北极熊
	  用途，仅用于捕影应急响应小组基础内训或挖矿应急演练之用
