# btpanel-v7.7.0
btpanel-v7.7.0-backup  官方原版v7.7.0版本面板备份

**Centos/Ubuntu/Debian安装命令 独立运行环境（py3.7）**

```Bash
curl -sSO https://raw.githubusercontent.com/8838/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```

**备用安装链接，适用于不能访问GitHub的服务器。文件公开存放在[d.moe.ms](http://d.moe.ms/?btpanel-v7.7.0)**

```
curl -sSO http://d.moe.ms/AAAAA/btpanel-v7.7.0/install/install_panel.sh && bash install_panel.sh
```

# 手动破解：

1，屏蔽手机号

```
sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|" /www/server/panel/BTPanel/static/js/index.js
```

2，删除强制绑定手机js文件

```
rm -f /www/server/panel/data/bind.pl
```

3，手动解锁宝塔所有付费插件为永不过期

文件路径：`/www/server/panel/data/plugin.json`

搜索字符串：`"endtime": -1`全部替换为`"endtime": 999999999999`

4，给plugin.json文件上锁防止自动修复为免费版

```
chattr +i /www/server/panel/data/plugin.json
```

============================

！！如需取消屏蔽手机号

```
sed -i "s|if (bind_user == 'REMOVED') {|if (bind_user == 'True') {|g" /www/server/panel/BTPanel/static/js/index.js
```

============================
# 优化补丁

补丁来自:https://blog.cccyun.cn/post-431.html

这个是自用的宝塔面板一键优化补丁，主要有以下优化项目：

1.去除宝塔面板强制绑定账号

2.去除各种删除操作时的计算题与延时等待

3.去除创建网站自动创建的垃圾文件（index.html、404.html、.htaccess）

4.关闭未绑定域名提示页面，防止有人访问未绑定域名直接看出来是用的宝塔面板

5.关闭活动推荐与在线客服，去除首页企业版广告

6.去除自动校验文件与上报信息定时任务

7.去除面板日志与网站绑定域名上报

适用于宝塔Linux面板7.7版本的命令
```
wget -O optimize.sh https://raw.githubusercontent.com/liangnicho/btpanel-v7.7.0/main/optimize.sh && bash optimize.sh
```
适用于宝塔Linux面板>=7.9版本的命令（7.9版本不支持去除强制绑定账号）：
```
wget -O optimize.sh https://raw.githubusercontent.com/liangnicho/btpanel-v7.7.0/main/optimize_new.sh && bash optimize.sh
```
适用于宝塔国际版aaPanel的命令：
```
wget -O optimize.sh https://raw.githubusercontent.com/liangnicho/btpanel-v7.7.0/main/optimize_aapanel.sh && bash optimize.sh
```
