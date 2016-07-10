---
layout: post
title: FIDO UAF Protocol
---

## 1. 概览

&ensp;&ensp;FIDO使用UAF的目的是使FIDO依赖方选择一个对于特定终端用户或交互最好的认证机制，同时使依赖方具备无需额外集成工作就可在未来能够充分利用信的设备安全功能的能力。
  
### 1.1 体系机构

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF1.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图1 UAF体系结构

&ensp;&ensp;上述体系结构的实体中，只有三个实体会之间创建或处理UAF协议信息：

 - IDO Server：运行在依赖方的基础设施 
  
 - IDO UAF Client：运行在FIDO用户设备上的Client； 
  
 - IDO Authenticator：整合进FIDO用户设备中。 

### 1.2  协议会话

UAF核心协议包含4个在FIDO UAF Client和 FIDO Server之间进行的概念上的会话。

&ensp;&ensp;Registration：UAF允许依赖方在依赖方本地注册FIDO Authenticator并与用户帐户绑定。依赖方可以制定策略指定支持不同的Authenticator类型。用户只能注册符合现有策略的Authenticator。

&ensp;&ensp;Authentication：UAF允许依赖方提示用户使用之前注册的Authrnticator进行身份验证。验证可以被依赖方在任何时间调用。

&ensp;&ensp;Transaction Confirmation: 除了提供一般的认证提示，UAF支持对用户的具体事物行为的提示。这种提示包括传递给客户端要向用户展示的附加信息，使用户可以利用这个信息进行交易确认。这种额外认证操作是为了使依赖方得到用户确实确认了这笔交易的保证（而不是仅仅对Session进行认证）。

&ensp;&ensp;Deregistration: 依赖方可以触发删除账户捆绑的认证密钥的行为。

### 1.3 协议会话概览

#### 1.3.1 Registration

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF2.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图2 UAF Registration 信息流

#### 1.3.2 Authentication

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF3.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图3 UAF Authentication 信息流

#### 1.3.3 Transaction Confirmation

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF4.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图4 UAF Transaction Confirmation 信息流

#### 1.3.4 Deregistration

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF5.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图5 UAF Deregistration 信息流

## 2. 协议细节

&ensp;&ensp;除特殊说明，所有UAF软件都必须支持协议中的所有元素；

&ensp;&ensp;所有字符串中的字符串是Unicode字符，开始于U+0000，结束于U+007F;

&ensp;&ensp;除特殊说明，所有协议消息传输过程中使用UTF-8编码。

&ensp;&ensp;所有的协议信息交互必须在TLS/HTTPS安全通道下。

### 2.1 Registration

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF6.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图6 UAF Registration 流程图

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF7.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图7 UAF Registration 密文数据流图

&ensp;&ensp;1）FIDO Server发送AppID、authenticator policy、ServerChallenge和用户名到FIDO Client；

&ensp;&ensp;2） FIDO Client计算使用ServerChallenge计算得到FInalChallengeParams（FCH）以及一些其他值，把AppID、FCH和UserName传给Authenticator。

&ensp;&ensp;3） Authenticator使用这些值生成Key Registration Data（KRD），然后把新产生的用户公钥等其他数据以及这些数据的签名发送到服务器，服务器对生成的KRD进行验签，通过后存储用户公钥等数据。

### 2.2  Authentication

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF8.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图8 Authentication 流程图

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF9.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图9 Authentication 密文数据流图

## 3. 其他注意事项

### 3.1 协议核心设计安全点

#### 3.1.1 Authenticator Metadata

&ensp;&ensp;因为在协议设计的过程中假设FIDO Server可以访问到所有设备支持的Authenticator和他们对应的Authenticator Metadata。Auth. Metadata中包含1）支持的注册和认证模式 2）认证因子，安装方式，支持的内容形式以及其他附加数据。为了决定对于特定的过程使用哪一个Authenticator进行认证，FIDO Server会通过AAID在Authenticator列表中查找并获取需要的信息。AAID：Authenticator Attestation ID。每一个Auth. Metadata实体必须被一个唯一的AAID认证。

#### 3.1.2 Authenticator Attestation

&ensp;&ensp;Authenticator Attestation是指在注册阶段对Authenticator进行认证的过程。这一步使依赖方能够以密码学方式验证FIDO Client声明的Authenticator确实是它声明的那个。

&ensp;&ensp;Authenticator必须支持Basic Attestation。注意：Authenticator对Attestation Key做的保护是自定义的。

&ensp;&ensp;Basic Attestation有两种方式：

 - Full Basic Attestation：基于被同一类Authenticator共享的attestation private key。
 
 - Surrogate Basic Attestation：仅仅是语义上的Basic Attestation，attestation object是自签名的，比如使用UAthen.priv key签名。因此不能提供密码学安全证明。但是这是在我们不能获取到attestation private key时的最好解决办法。

&ensp;&ensp;Full Basic Attestation证书链如下图10所示：

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF10.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图10 Attestation证书链

&ensp;&ensp;FIDO服务器必须能访问能够认证Attestation公钥的信任根。Authenticator在注册的时候必须提供它的Attestation签名。

&ensp;&ensp;Surrogate Basic Attestation方式中，UAuth.priv key必须被用来对注册数据进行签名。这一行为必须被声明在Auth. Metadata中。对于没有对Attestation Key提供足够保护的Authenticator，必须要使用这种方式做认证。

#### 3.1.3 错误处理

&ensp;&ensp;FIDO Server 产生的任何错误信息都必须通知调用它的依赖方；

&ensp;&ensp;Authenticator在协议进行中产生的任何错误信息都必须通知UAF Client。

#### 3.1.4 断言方案

&ensp;&ensp;称以下两部分:

- Cryptographic key provisioning (KeyRegistrationData)

- Cryptographic authentication and signature (SignedData)

方案为断言方案。

&ensp;&ensp;注册断言方案定义了在Authenticator和FIDO Server是如何交换密钥，交换何种格式的密钥。

&ensp;&ensp;认证断言方案定义了Authenticator以何种方式、何种格式生成签名。

#### 3.1.5 TLS通信

&ensp;&ensp;主要对TLS端点和使用的版本和算法进行了规范。

### 3.2 安全点

&ensp;&ensp;UAF协议在协议层面已经具有了很高的安全性，因此协议不是安全弱点。

#### 3.2.1 Authenticator安全性

#### 3.2.2 密码算法安全性

&ensp;&ensp;推荐使用ECDSA和SHA256/SHA512，也支持RSA。使用ECDSA的时候需要在每一次签名的过程中用到一个新鲜的随机数。因此随机数生成算法需要强壮的随机数生成算法。

#### 3.2.3 应用隔离

![_config.yml]({{ site.baseurl }}/images/2016-7-10-UAF11.PNG)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图11 FIDO实体间认证概览

&ensp;&ensp;使用KHAccessToken来做应用之间的隔离。所谓的KHAccessToken是一个有Authenticator生成的用来做访问限制的密钥。

#### 3.2.4 TLS binding

&ensp;&ensp;Channel binding.

#### 3.2.5  Session管理

&ensp;&ensp;Session管理依赖于依赖方Web应用的Session管理。

#### 3.2.6 防重放攻击

&ensp;&ensp;使用了2种方式防止重放攻击：

&ensp;&ensp;TLS和服务器端挑战。

#### 3.2.7 防止Authenticator被克隆

&ensp;&ensp;由于UAF依赖于Authenticator中管理和保护的UAuth key，因此要保证Authenticator不被克隆。只要有两种方法：

&ensp;&ensp;第一，如果以合适的方法保护私钥，那么克隆Authenticator与拿到私钥一样困难；

&ensp;&ensp;第二，UAF定义了一个签名计数器。每做一次签名，计数器就会增加。如果使用了一个克隆的Authenticator，那么后来使用的原始Authenticator就会产生一个比现在低或者等于的计数器值，这样就会被FIDO服务器端发现。

