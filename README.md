# v2fly-ibm-workers [![](https://github.com/tlmoe/v2fly-ibm-workers/workflows/Deploy%20to%20IBM%20Cloud/badge.svg)](https://github.com/tlmoe/v2fly-ibm-workers/actions)


大佬的原帖链接：
https://www.hostloc.com/thread-722265-1-1.html
我只研究了方法一，比较简单点，下面直接说那11个secret:

CF_UUID_IBM=设定的UUID
CF_WSPATH_IBM=设定V2的path
CF_ROUTE_IBM=项目名称.mybluemix.net
CF_WORKER_NAME_CF=cloudflare里面建立works起的名称
CF_ACCOUNT_ID_CF=cloudflare里works里的帐户 ID
CF_USER_IBM=IBM的用户名
CF_PASSWORD_IBM=IBM的密码
CF_ORG_IBM=IBM的组织名
CF_SPACE_IBM=IBM的空间名
CF_API_KEY_CF=cloudflare的API 密钥--Global API Key
CF_EMAIL_CF=cloudflare的邮箱

然后FORK，改一下定时重启的时间和频率，删除之前的IBM项目，Action！

补充：不成功的，我看了下，一般以下几个问题：
1、一定要删除之前的项目，比如IBMyes等，不然不会成功

2、以下修改下，写了建议的，可以不改，其他请一定修改以下，保证后期不出问题：

行                      参数                             说明

8                  - cron: "0 21 * * 4"             #4改为*，即为每天重新部署一次，当然，你也可以改成2天一次，3天一次（小白就直接4改*）

56                - name: v2fly                      #修改为你自己的项目名称，CF_ROUTE_IBM这个secret就是填这个名称，建议改为IBMyes时候你设定的项目名称，这样能CF works延用之前的works，不会因为换名称而新建works，到时候填伪装域名又要换！

57                  memory: 128M                 #建议修改到256

58                  disk_quota: 128M              #建议修改到1024

CF_ROUTE 是IBM应用 的访问网址，
不过一般是通过workers转发，这个地址不怎么重要。

譬如设置了
CF_UUID_IBM:       cd8cd4db-5610-4389-a7dd-415763763a0

CF_WSPATH_IBM:  /ktAL931X7

CF_WORKER_NAME_CF： my-ibm-worke

v2n客户端配置图：

