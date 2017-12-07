> sourcetree是一款Git图形化管理工具

### 1. Generating an SSH key
[Generating an SSH key](https://qingfengmy.github.io/2016/12/23/Generating-an-SSH-key/)

### 2. 使用私钥和公钥
生成.ssh的公钥和私钥后，公钥放在github或gitlab上，私钥要加到本地的SSH-AGENT。sourcetree提供了类ssh-agent的工具--pagent，但要求的私钥格式不同。
直接加载私钥会提示错误"Couldn't load this key (OpenSSH SSH-2 private key)".

解决方式是：
> sourcetree>工具>创建或导入SSH秘钥（Putty）>Conversions>import key（选择私钥）>save private key（保存为后缀名为.ppk的文件）

> sourcetree>工具>启动SSH助手>添加.ppk文件即可

#### 参考文章
[git Couldn't load this key (OpenSSH SSH-2 private key)](http://blog.csdn.net/irabbit0708/article/details/54089439)
### 3. 跳过sourcetree的翻墙注册
#### 第一步：打开sourcetree，到注册页关闭。
#### 第二步：打开 `我的电脑`，在最上方的地址栏直接输入以下地址：
```
%LocalAppData%\Atlassian\SourceTree\
```
#### 第三步：在这个目录下新建一个名为 accounts.json 的文件
把以下文本粘贴过去
```
[
  {
    "$id": "1",
    "$type": "SourceTree.Api.Host.Identity.Model.IdentityAccount, SourceTree.Api.Host.Identity",
    "Authenticate": true,
    "HostInstance": {
      "$id": "2",
      "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountInstance, SourceTree.Host.AtlassianAccount",
      "Host": {
        "$id": "3",
        "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountHost, SourceTree.Host.AtlassianAccount",
        "Id": "atlassian account"
      },
      "BaseUrl": "https://id.atlassian.com/"
    },
    "Credentials": {
      "$id": "4",
      "$type": "SourceTree.Model.BasicAuthCredentials, SourceTree.Api.Account",
      "Username": "",
      "Email": null
    },
    "IsDefault": false
  }
]
```
#### 参考文章：[Windows 版 SourceTree 免登录跳过初始设置的方法](http://www.jianshu.com/p/3478e2a214a1)
