+++
date = 2020-03-22T16:19:43
description="折腾一下Kali 系统"
tags = ["tech","play"]
title = "Kali_?"
+++

# web 应用：

有几个组件：server app DB browser

- Web Browser/Client （通常为我们的浏览器）
- Web Server（通常为网站所在服务器）
- Web app（通常为部署网站的后台应用）
- DB（数据库，数据存储所在）

1）URL 解释攻击URL interpretation attacks 浏览器 中 URL 解释会有 请求参数的暴露

2）输入验证攻击 input Validation attacks浏览器 越过防火墙 请求服务器时，如果 **未经筛选**，其皆为输入，就有机可乘。

3）SQL注入 injection attacks:当请求需要访问到数据库时，如：登录，注册等等，服务器没有好的控制就会造成无密码登录，或修改敏感数据等操作；

4）缓冲区溢出攻击 buffer overflow attacks ：犹如 DDOS攻击，使得其无法服务，而无法提供正常服务。

攻击方式：

- XSS（Cross Site Script，跨站脚本攻击）
- Cross Site Request Forgery (CSRF， 跨站请求伪造)
- Session hijacking attack（Session 挟持）
- File inclusion vulnerability（文件包含漏洞）
- file upload attack（文件上传攻击）
- Weak Password Vulnerability（弱密码暴力破解）
- webshell（web 后门攻击）
- SQL Injection（SQL 注入）
- Distributed Denial of Service （DDoS， 分布式拒绝服务）

docker run -ti --network host 3f457 bash 

docker 为kali Linu下 容器，QEMU 为MEtasp2 提供支持。

``` bash
#启动
sudo virsh start Metasploitable2
ping target
```

查看 系统监听的端口： net 网 stat 状态

```sh
netstat  -tln 
```

t =>tcp l=>listing n=>？？？

查看当前系统开发的服务： rpc 通信框架

```bash
rpcinfo -p localhost
```

---

- 确定目标：首先你要有一个渗透测试的目标，或者是攻击的目标。
- 信息采集：通过各种信息搜集工具，如目标的域名、IP、端口、后台应用运行的平台等等了解，只有当对后台的应用框架有了一定的了解我们才能有针对性的使用某一方面的技术或者漏洞进行攻破。
- 漏洞扫描：在对目标应用的运行平台有了一定的了解之后，我们可以搜集相关组件的所存在的漏洞进行预判可能存在的漏洞，或者通过漏洞扫描工具来发现错在的漏洞。
- 漏洞验证：发现漏洞之后便是对漏洞的一个验证，简单来说就是进行对目标的攻击，攻击目标便是对漏洞的利用登入设备然后进行提权，这样便可“为所欲为”。
- 权限维持：在攻破系统之后，会在创建一个权限较高的隐藏用户亦或者放置后门程序，以便下一次的登陆，而不用再次去攻击。
- 文档记录：在每一次攻击之后建议都用文档记录下来，以后对知识的总结与积累。

---

工具 ：

- whois
- host
- dig
- nmap 端口扫描；network mapper
- Metasploit 

挖掘 域名相关信息，服务器，他搭建起来框架的常见漏洞如 Nginx、tomcat 等等，通过社会工程学与 Google Hacking 查找、猜测可能存在的一些问题和信息）
找准方向

| Port | Describe                      |
| ---- | ----------------------------- |
| 21   | FTP                           |
| 22   | SSH                           |
| 23   | Telnet                        |
| 80   | HTTP use Nginx or Apache 等等 |
| 443  | HTTPS                         |
| 3306 | Mysql                         |
| 3389 | RDP                           |
| 5432 | PostgreSQL                    |
| 5900 | VNC                           |
| 6379 | Redis                         |
| 8080 | Tomcat 等                     |

> 有一些网络基础的同学会知道，在理论上我们将网络分为七层，而 nmap 在使用该参数的时候处于的层次是自适应，因为当你扫描的目标地址若是局域网内部的 IP 地址、同一子网的地址时此命令首先会在局域网中广播 ARP 请求，看目标主机是否为内网设备（若是学习过由浅入深学网络的同学就会了解 ARP 协议是一个二层协议，用于 IP 地址与 MAC 地址之间的解析），若是内网设备便会直接响应，自然便是处于二层的扫描，但若是一外网地址内网的广播自然不会有主机响应其请求，此时便会使用 ICMP 协议，而 ICMP 协议便是一个网络层的协议，我们通常使用的 ping 命令便是使用的 ICMP 协议。而正因为使用的是 ping 命令来探知对方是否开机所以在获得的信息中不会得到 MAC 地址。

针对 [ARP（地址解析协议）](https://baike.baidu.com/item/ARP) 的探测

针对 网络层 探测

---

漏洞： Nessus & joomscan

难搞...不看了。