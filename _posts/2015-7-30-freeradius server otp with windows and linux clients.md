---
layout: post
title: freeradius server otp with windows and linux clients
---

1.	ϵͳ�汾 CentOS-6.4-i386 

		freeradius�汾��FreeRADIUS Version 2.1.7
		
		otpd�汾��otpd version 3.2.4
		
		��װfreeradius ʱ���֣�
			
			1�� checking for _talloc in -ltalloc in /opt/lib... no
		
					configure: WARNING: talloc library not found. Use --with-talloc-lib-dir=<path>.
	
					configure: error: FreeRADIUS requires libtalloc ʱ��
	
					ʹ�ã� yum install libtalloc-devel -y
			
			2������ȱ�� XXX.so��ʱ�� ʹ�� yum provide */XXX.so ���Ǹ����װ�Ǹ�
			
			��װotpd serverʱ��
			
			

2.	Linux freeradius pam�� http://freeradius.org/pam_radius_auth/
		
		������ʱ���� pam_modules.h not found ����ʱ�� yum install gcc pam-devel ��װpam��������
		
		make ���� pam_radius_auth.so 
		
		cp pam_radius_auth.so /lib/security/pam_radius_auth.so
		
		�޸� /etc/pam.d �ļ����µ�Ӧ�ó���pam����
		
		ʹ��tty��¼ʱ�޸�login�ļ�
		
		ʹ��ͼ�ν����¼ʱ�޸�gdm��gdm-passwd�ļ�
 
3. windows ��֤��� pgina
		