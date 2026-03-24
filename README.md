# V1.2更新
添加“CVE-2025-49844任意命令执行”和“Gopher协议Payload生成”模块

# redis_tools_GUI
基于 Python 3 编写的 redis 漏洞图形化利用工具。

> **⚠️ 免责声明**：本工具仅供安全研究和授权渗透测试使用。严禁用于非法攻击。使用者需自行承担因不当使用造成的任何后果。

## ✨ 实现功能

  * **redis密码爆破**
  * **CLI控制台**
  * **计划任务反弹shell**  会清空目标root计划任务数据！！
  * **写ssh公钥拿shell** 
  * **目录探测**
  * **任意文件写入（写webshell）**
  * **CVE-2022-0542任意命令执行**
  * **CVE-2025-49844任意命令执行**  （目前仅支持8.2.1版本）
  * **主从复制命令执行（内置payload）**  会清空目标redis数据！！
  * **Gopher协议Payload生成**
![自定义图片名称](https://img.haotaoyun.com/2026/03/1774352700_1.jpg)
![自定义图片名称](https://img.haotaoyun.com/2026/03/1774352703_2.jpg)
![自定义图片名称](https://img.haotaoyun.com/2026/03/1774352704_3.jpg)
![自定义图片名称](https://img.haotaoyun.com/2026/03/1774352705_4.jpg)
![自定义图片名称](https://img.haotaoyun.com/2026/03/1774352705_5.jpg)
![自定义图片名称](https://img.haotaoyun.com/2026/03/1774352706_6.jpg)


## 🚀 使用方法
1 已经打包好了，可以直接运行redis_tools_GUI_v_2_1.exe

2 可以下python执行：python redis_tools.py

python运行需要有库 pip install redis
	


## payload参考
里面so和dll payload我没有自己去做，这里借用的下面师傅的，直接内嵌进去的
https://github.com/yuyan-sec/RedisEXP
CVE-2025-49844参考下面师傅的逻辑
https://github.com/saneki/cve-2025-49844



## 云服务器获取
redis很多利用都需要公网服务器。以供大家参考。
---

> **好淘云 (haotaoyun.com) · 实时更新全网云服务器优惠 · 分享建站及运维小技巧**
> 
> **提示：首购特惠机型建议一次性买满3年，后续续费恢复原价会比较贵！另外建议打开链接后先登录，有时候登录后看更便宜，以下链接页面都有满减和打折优惠券，往下翻一翻**

|云厂商|特惠活动专区|核心配置|优惠价格|官方直达|
|:--|:--|:--|:--|:--|
|**阿里云**|学生专属|2核2G|**免费半年**|[立即领取](https://www.haotaoyun.com/go/aliyun-student)|
|**阿里云**|新人抢购|2核2G|**38元/年**|[点击抢购](https://www.haotaoyun.com/go/aliyun)|
|**阿里云**|任意用户，老客同享|2核2G，2核4G|**99元，199元/年**|[点击抢购](https://www.haotaoyun.com/go/aliyun)|
|**腾讯云**|买1年送3个月|2核2G，4核8G|**99元，450元/年**|[点击抢购](https://www.haotaoyun.com/go/tencent)|
|**腾讯云**|香港/海外免备案专区|2核2G|**24元/月**|[点击抢购](https://www.haotaoyun.com/go/tencent-hk)|
|**京东云**|每天三场抢购，概率极高|2核2G，2核4G|**68元，158元/年**|[点击抢购](https://www.haotaoyun.com/go/jd)|
|**野草云**|香港/海外免备案专区|2核2G|**99元/年**|[点击抢购](https://www.haotaoyun.com/go/yecaoyun)|
