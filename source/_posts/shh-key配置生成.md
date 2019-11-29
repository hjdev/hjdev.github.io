#### 生成秘钥 

输入如下命令以生产gitlab服务端和本地git相互传输时所需要校验的私钥和公钥。双引号内输入的是你git注册用户邮件。

```
$ git config --global user.name"你的用户名"

$ git config --global user.email"你的邮箱"

$ ssh-keygen -t rsa -C"你的邮箱"

------------------------------------------------------------------------------------
默认会在/c/Users/Administrator/.ssh目录中生成秘钥，如果提示已经存在 可重写，成功后如下显示：
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Administrator/.ssh/id_rsa.
Your public key has been saved in /c/Users/Administrator/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:LpEhcgm0rrnzsEMjo/e1g8n5Xsdw/TXdvSRjihAfkGo 8888888@qq.com
The key's randomart image is:
+---[RSA 2048]----+
| .o    ..        |
|   o . ..        |
|  o + o. .       |
| . o E oo ..    +|
|  . . o.S.. .+ o=|
|o=     o.+. o.+.o|
|B... +o o.o.  .. |
|++. =..+ .       |
|o=...o+.         |
+----[SHA256]-----+

```

#### 配置公钥

把在/c/Users/Administrator/.ssh目录中生成的公钥id_rsa.pub(第二个文件) 粘贴在gitHub 账户设置的SSH KEY中，title可以随便取

![1](shh-key配置生成/3.png)

![1](shh-key配置生成/1.png)

#### 代码拉取

获取代码使用git clone 的地址时候选择ssh协议的地址链接

![1](shh-key配置生成/2.png)