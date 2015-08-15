---
layout: post
title: freeradius server otp with windows and linux clients
---

1.    系统版本 CentOS-6.4-i386 

		freeradius版本：FreeRADIUS Version 2.1.7
		
		otpd版本：otpd version 3.2.4
		
		安装freeradius 时出现：
			
			1） checking for _talloc in -ltalloc in /opt/lib... no
		
					configure: WARNING: talloc library not found. Use --with-talloc-lib-dir=<path>.
	
					configure: error: FreeRADIUS requires libtalloc 时：
	
					使用： yum install libtalloc-devel -y
			
			2）出现缺少 XXX.so库时， 使用 yum provide */XXX.so 看那个库就装那个
			
			安装otpd server时：
			
			1)./configure 如果提示没有openssl 安装 apt-get install libssl-dev
			
   			centos 下 yum install openssl openssl-devel
   			
			2) getpeereid.c:65: error: storage size of ‘peercred’ isn’t known错误
			
   			configure 后加 CPPFLAGS="-I/home/XXX/app/BerkeleyDB/include -D\_GNU\_SOURCE"
			
			

2.	Linux freeradius pam： http://freeradius.org/pam_radius_auth/
		
		当编译时出现 pam_modules.h not found 错误时： yum install gcc pam-devel 安装pam开发工具
		
		make 生成 pam_radius_auth.so 
		
		cp pam_radius_auth.so /lib/security/pam_radius_auth.so
		
		修改 /etc/pam.d 文件夹下的应用程序pam配置
		
		使用tty登录时修改login文件
		
		使用图形界面登录时修改gdm和gdm-passwd文件
 
3. windows 认证插件 pgina
		
