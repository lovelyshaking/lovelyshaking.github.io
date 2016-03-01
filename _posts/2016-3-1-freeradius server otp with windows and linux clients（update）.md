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
			
   			configure 后加 CPPFLAGS="-D_GNU_SOURCE"
   			
   		安装otp perl脚本时：
			
			1)Can't locate CPAN.pm in @INC (@INC contains: /usr/local/lib/perl5 /usr/local/share/perl5 /usr/lib/perl5/vendor_perl /usr/share/perl5/vendor_perl /usr/lib/perl5 /usr/share/perl5 .)
			
   			Checking ‘perl-CPAN’ package run following in your shell 
   			
   			[root@host13 ~]# rpm -q perl-CPAN

			If perl-CPAN package is installed, you will get the output like this

			perl-CPAN-1.9402-116.fc13.i686

			else, you will get output like this

			package perl-CPAN is not installed

			and that the case you need to install it. You can install it via using yum, yum install perl-CPAN or from rpm, from “rpm.pbone.net” you can obtain “perl-CPAN rpm’s”.
   			
			2) error “make test had returned bad status, won’t install without force”
			
   			First go into perl CPAN shell：perl -MCPAN -e shell
   			
			then you can do force install of module using the command : force install Authen::HOTP
			
			

2.	Linux freeradius pam： http://freeradius.org/pam\_radius\_auth/
		
		当编译时出现 pam_modules.h not found 错误时： yum install gcc pam-devel 安装pam开发工具
		
		make 生成 pam_radius_auth.so 
		
		cp pam_radius_auth.so /lib/security/pam_radius_auth.so
		
		修改 /etc/pam.d 文件夹下的应用程序pam配置
		
		使用tty登录时修改login文件
		
		使用图形界面登录时修改gdm和gdm-passwd文件
 
3. windows 认证插件 pgina
		
