---
layout: post
title: FIDO UAF Overview
---

## 介绍

&ensp;&ensp;FIDO联盟的目标是通过以下方式改变在线强身份认证：

  - 制定开放、可扩展的、可交互的在线用户身份认证机制以取代基于密码的身份认证；
  - 执行行业计划以保证全球范围内接受标准；
  - 向标准化组织提供成熟的技术方案。
  
&ensp;&ensp;FIDO的核心思想是：易用、高安全和隐私、标准化。

&ensp;&ensp;在FIDO体系结构中，包含两个关键协议以满足用户在使用互联网服务时的两种基本选择。这两个协议有很多共同点但是被分配了不同的使用情况。

&ensp;&ensp;FIDO UAF Protocol，全称Universal Authentication Framework Protocol，FIDO通用认证框架协议。UAF协议允许在线服务提供无密码和多因子安全服务。用户使用一种本地认证机制向在线服务注册设备，本地认证机制包括指纹、图像、声音、或者PIN。UAF协议允许在线服务指定用户使用哪种方式做本地认证。
注册完毕后，用户在需要认证时简单的完成本地认证即可。用户做本地认证的时候不再需要输入密码。UAF支持多重认证机制，如指纹+PIN。

&ensp;&ensp;FIDO U2F Protocol，全称Universal 2nd Factor Protocol，通用双因素认证协议。U2F协议允许在线服务在现有密码基础设施不变的情况下加入双因子认证加强用户登录的安全性。用户在登录时仍然输入用户名和密码，在线服务会提示用户提供一个双因子设备。强双因子认证可以允许在线服务简化用户密码强度（如4位PIN）而不影响安全性。

## 架构

![_config.yml]({{ site.baseurl }}/images/2016-6-14-UAF1.jpg)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图1 UAF架构

### FIDO UAF Client

&ensp;&ensp;&ensp;&ensp;  - UAF Client 用于执行客户端的UAF协议。其职责在于：

&ensp;&ensp;&ensp;&ensp;  - 与特定的UAF Authenticator在UAF Authenticator Abstraction Layer通过UAF Authenticator API进行交互；
	
&ensp;&ensp;&ensp;&ensp;  - 与设备上的用户代理（User Agent）（如：APP，浏览器）进行交互，该用户代理使用用户代理特定接口与UAF Server进行通信。例如，FIDO标准的浏览器插件可以使用已有的浏览器插件接口，APP可以使用FIDO标准SDK，随后User Agent就负责与依赖方（Relying Party）的UAF Server交互的UAF Message的通信。
	
&ensp;&ensp;FIDO UAF架构保证FIDO Client可以被部署到不同的平台上。

### FIDO UAF Server

&ensp;&ensp;FIDO UAF Server用于执行服务器端UAF协议，其职责在于：

&ensp;&ensp;&ensp;&ensp;  - 与依赖方（Relying Party）的Web服务器交互，以传输UAF Protocol Message到UAF Client；

&ensp;&ensp;&ensp;&ensp;  - 认证UAF attestation，确保只有受信任的Authenticators才能被注册；

&ensp;&ensp;&ensp;&ensp;  - 管理UAF Authenticator与依赖方的用户帐号之间的关系；

&ensp;&ensp;&ensp;&ensp;  - 评估用户认证和对交互确认的响应来决定其有效性。

### FIDO UAF Protocol

&ensp;&ensp;UAF Protocol用来携带用户设备和依赖方交互使用的UAF Message。协议消息主要用于：

&ensp;&ensp;&ensp;&ensp;  - Authenticator Registration：UAF 注册协议使依赖方能够：

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;发现用户系统或设备上的UAF Authenticator是否可用。发现后将传输Authenticator Attribute到依赖方以完成策略决定和实时策略；

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;鉴别UAF Authenticator的认证断言以保证认证者是真实可信的。鉴别时使用通过Authenticator Metadata分发的身份认证公钥证书；

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;认证Authenticator并将其与在依赖方的用户帐户进行绑定。

&ensp;&ensp;&ensp;&ensp;  - 用户认证

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;认证通常基于密码学挑战-响应协议，帮助用户选择哪些Authenticator被部署在认证事件中。

&ensp;&ensp;&ensp;&ensp;  - 安全传输确认

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;如果用户的Authenticator支持这个功能，依赖方可以提供给用户一个用来确认的安全消息。消息内容是依赖方自定义的，可以使用在多个上下文中，如确认金融交易，用户协议，披露病人资料等。

&ensp;&ensp;&ensp;&ensp;  - 认证者注销

当用户帐户被依赖方移除是注销是必须的。依赖方可以通过请求移除相关联的UAF凭证触发注销。

### FIDO UAF Authenticator Abstraction Layer

&ensp;&ensp;&ensp;&ensp;FIDO UAF Authenticator Abstraction Layer向UAF Client提供了统一的API以使Client可以在FIDO支持的操作中使用基于Authenticator的密码服务。

### FIDO UAF Authenticator

&ensp;&ensp;&ensp;&ensp;UAF Authenticator是一个安全实体，存在或者连接与用户设备，可以创建与依赖方相关联的密钥材料(Key material)。密钥可以用于参与UAF强认证协议，如可以做对依赖方挑战的应答。

&ensp;&ensp;&ensp;&ensp;为了满足简化的目标，UAF Authenticator可以证明它的特定类型（如生物认证），它的能力（如所支持的密码算法）和出处。这为依赖方提供了高度的可信性，使依赖方可以确认该用户确实注册在该站点。

###  FIDO UAF Authenticator Metadata Validation 

&ensp;&ensp;&ensp;&ensp;在UAF上下文中，证明（Attestation）是指在注册过程中Authenticator向依赖方声明的生成的密钥，生成的报告是不是来自具有签名的真正的设备。UAF Server会校验携带在UAF注册协议中的证明签名。Metadata保存证明证书，并与Server在带外共享。（也就是说Metadata存的是用来Attestation的证书）。

##使用场景和消息流

### UAF Authenticator获取和用户登记

&ensp;&ensp;用户可以有多种方法获取Authenticator：买一个具有FIDO Authenticator功能的设备等。用户可以使用指纹等方式向Authenticator登记。

### Authenticator Registration

![_config.yml]({{ site.baseurl }}/images/2016-6-14-UAF2.jpg)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图2 Registration消息流

### Authentication

![_config.yml]({{ site.baseurl }}/images/2016-6-14-UAF3.jpg)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图3 Authentication消息流

### Step-up Authentication

&ensp;&ensp;Step-up Authentication是对网站基本用户登录认证的一种补充。通常在线服务或者网站允许未经身份验证的使用，如进行信息浏览。然而一旦用户要求更为有价值的活动时，比如进入会员专区，网站就会要求进行进一步的认证。这个过程甚至在交易的过程中分为好几步进行。

&ensp;&ensp;UAF可以顺利的进行这种交互。

### Transaction Confirmation

![_config.yml]({{ site.baseurl }}/images/2016-6-14-UAF4.jpg)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图4 Transaction Confirmation消息流

### Authenticator Deregistration

![_config.yml]({{ site.baseurl }}/images/2016-6-14-UAF5.jpg)

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;图5 Authenticator Deregistration消息流

## 隐私策略
&ensp;&ensp;FIDO制定了以下隐私策略：

1.	UAF设备不具有在所有依赖方之间可见的全局标识符，也不具备在特定依赖方的全局标识符。比如一个人UAF设备丢了之后另一个人捡到了他不能发现丢失设备这个人有某个依赖方的账户；如果两个人共享一个UAF设备。但是在同一依赖方上每个人都有一个帐号，那么依赖方无法分辨两个帐号共享一个设备。
2.	UAF Protocol为每一个设备、每一个用户帐户、每一个依赖方都生成一个唯一的非对称密钥对。不同依赖方使用的密钥不允许任何一方连接到同一个用户的所有活动；
3.	UAF Protocol操作要求最小信息收集。个人数据仅用于FIDO目的；
4.	UAF中用户验证本地执行，生物特征数据不传递也不保存在依赖方；
5.	使用时用户明确同意特定依赖方使用UAF设备；
6.	UAF Authenticator只能在设备生产商级别使用证明证书（Attestation Certificates）进行认证。

