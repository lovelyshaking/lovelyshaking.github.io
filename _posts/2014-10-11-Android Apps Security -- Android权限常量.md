---
layout: post
title: Android Apps Security -- Android权限常量
---

ACCESS\_CHECKIN\_PROPERTIES   ----------   允许读写访问checkin数据库中的properties表，改值可以更新上传

ACCESS\_COARSE\_LOCATION	------------    允许程序访问Cell\_ID或Wifi热点来获取粗略位置信息

ACCESS\_FINE\_LOCATION  ----------- 	允许程序访问精良位置（如GPS）

ACCESS\_LOCATION\_EXTRA\_COMMANDS	 ---------   允许应用程序访问额外的位置服务命令

ACCESS\_MOCK\_LOCATION 	---------    允许程序创建模拟位置服务用于测试

ACCESS\_NETWORK\_STATE ---------	允许程序访问有关网络信息

ACCESS\_SURFACE\_FLINGER  --------    允许程序使用Surfaceflinger底层特性

ACCESS\_WIFI\_STATE	---------   允许程序访问wifi网络状态信息

ACCOUNT\_MANAGER	 -----------    允许程序调用AccountAuthenticators

AUTHENTICATE\_ACCOUNTS   ------------  允许应用作为AccountManager的AccountAuthenticator

BATTERY\_STATES	 -------------    允许程序更新手机电池统计信息

BIND\_APPWIDGET	-------------   允许应用程序告诉AppWidget的服务应用程序可以访问AppWidget的数据

BIND\_DEVICE\_ADMIN	------------  设备管理接收机是必须的，以确保只有系统可以与它进行交互

BIND\_INPUT\_METHOD	------------  InputMethodService是必须的，以确保只有系统可以绑定到它

BIND\_REMOTEVIEWS	-----------   RemoteViewsService是必须的，以确保只有系统可以绑定到它

BIND\_WALLPAPER	-----------   WallpaperService是必须的，以确保只有系统可以绑定到它

BLUETOOTH	-----------   允许引用连接到已配对的蓝牙设备

BLUETOOTH\_ADMIN	-----------   允许应用发现和配对蓝牙设备

BRICK	-----------   请求能够禁用设备（非常危险）

BROADCAST\_PACKAGE\_REMOVED	-----------   允许应用在被移除后能收到广播通知

BROADCAST\_SMS	-----------   允许应用能够广播SMS接收通知

BROADCAST\_STICKY	-----------   允许应用广播Sticky Intent

BROADCAST\_WAP\_PUSH	-----------   允许应用程序广播一个WAP推-收通知

CALL\_PHONE	-----------   允许应用发起一个电话，用户不用通过拨号用户界面，以确认被置于通话

CALL\_PRIVILEGED	-----------   允许应用拨打任何号码，包含紧急号码，而无需通过拨号用户界面进行确认

CAMERA	-----------   请求访问使用照相设备

CHANGE\_COMPONENT\_ENABLE\_STATE	-----------   允许一个应用改变另一个应用程序组件的启用状态（禁用或启用）

CHANGE\_CONFIGURATION	-----------   允许应用修改当前设置，如本地化

CHANGE\_NETWORK\_STATE	-----------   允许应用改变网络连接状态

CHANGE\_WIFI\_MULTICAST\_STATE	-----------   允许应用进入wifi多播模式

CHANGE\_WIFI\_STATE    -----------   	允许应用改变wifi连接状态

CLEAR\_APP\_CACHE	-----------  允许应用清除设备上所有已安装的应用程序缓存

CLEAR\_APP\_USER\_DATA	-----------  允许应用清除用户数据

CONTROL\_LOCATION\_UPDATES	-----------  允许启用或禁止来自无线模块的位置更新提示

DELETE\_CACHE\_FILES	-----------  允许应用删除缓存文件

DELETE\_PACKAGES	-----------  允许应用删除包

DEVICE\_POWER	-----------  允许访问底层电源管理

DIAGNOSTIC  -----------  	允许应用RW诊断资源

DISABLE\_KEYGUARD	-----------  允许应用禁用键盘锁

DUMP	-----------  允许应用检索系统服务的状态转储信息

EXPAND\_STATUS\_BAR	-----------  允许应用扩展或收缩在状态栏

FACTORY\_TEST	-----------  允许作为一个工厂测试程序运行，以root用户运行

FLASHLIGHT	-----------  允许访问闪光灯

FORCE\_BACK	-----------  允许应用强制执行返回操作，无论是否在顶层Activity

GET\_ACCOUNTS	-----------  允许访问账户服务中的账户列表

GET\_PACKAGE\_SIZE	-----------  允许应用获取任何package占用空间容量

GET\_TASKS	-----------  允许应用获取有关当前或最近运行的任务的信息：任务的缩略图表示、什么样的活动正在运行中等

GLOBAL\_SEARCH	-----------  在Content Provider上使用该权限，能允许全局搜索系统来访问他们的数据

HARDWARE\_TEST	-----------  允许访问硬件外设

INJECT\_EVENTS	-----------  允许应用将用户时间注入时间流中（如按键、触摸及追踪球），并传递给任何窗口

INSTALL\_LOCATION\_PROVIDER	-----------  允许应用程序安装一个位置服务到位置管理器

INSTALL\_PACKAGES	-----------  允许应用安装包文件

INTERNAL\_SYSTEM\_WINDOW	-----------  允许应用打开窗口，其作为系统用户界面部分使用

INTERNET	-----------  允许应用打开网络套接字

KILL\_BACKGROUND\_PROCESSES	-----------  允许应用调用 killBackgroundProcesses(String)

MANAGE\_ACCOUNTS	-----------  允许应用管理AccountManager 中的账户

MANAGE\_APP\_TOKENS	-----------  允许应用管理窗口管理器中的应用令牌（如create、distory和Z-order）

MASTER\_CLEAR	-----------  目前还没有明确的解释,Android开发网分析可能是清除一切数据,类似硬格机

MODIFY\_AUDIO\_SETTINGS	-----------  允许应用修改全局音频设置

MODIFY\_PHONE\_STATE	-----------  允许修改话机状态，如电源，人机接口等

MOUNT\_FORMAT\_FILESYSTEMS	-----------  允许格式化可移动存储设备的文件系统

MOUNT\_UNMOUNT\_FILESYSTEMS	-----------  允许安装和卸载可移动存储设备的文件系统

NFC	-----------  允许应用通过NFC执行IO操作

FERSISTENT\_ACTIVITY	-----------  该常量已过时。此功能在未来将被删除，请不要使用。允许应用Activity持久

PROCESS\_OUTGOING\_CALLS	-----------  允许应用监视、修改或终止呼出

READ\_CALENDAR	-----------  允许应用读取用户日历数据

READ\_CONTACTS	-----------  允许应用读取用户联系人数据

READ\_FRAME\_BUFFER	-----------  允许应用进行屏幕截图和更多常规的访问帧缓冲数据

READ\_HISTORY\_BOOKMARKS	-----------  允许应用读取（但不能写入）用户浏览历史或书签

READ\_INPUT\_STATE	-----------  允许应用返回当前按键状态

READ\_LOGS	-----------  允许应用读取底层系统日志文件

READ\_PHONE\_STATE	-----------  允许应用读取（不能写）手机状态

ERAD\_SMS	-----------  允许应用读取短信

READ\_SYNC\_SETTINGS	-----------  允许应用读取同步设置

READ\_SYNC\_STATS	-----------  允许应用读取同步状态

REBOOT	-----------  重新启动设备必须要有此权限

RECEIVE\_BOOT\_COMPLETED	-----------  允许应用接收在系统完成启动后发出的ACTION\_BOOT\_COMPLETED广播

RECEIVE\_MMS	-----------  允许应用监控将收到的MMS彩信，并作记录或处理

RECEIVE\_SMS	-----------  允许应用监控将收到的SMS短信，并作记录或处理

RECEIVE\_WAP\_PUSH	-----------  允许应用监控将收到的WAP推送信息

RECORD\_AUDIO	-----------  允许应用录制音频

REORDER\_TASKS	-----------  允许应用改变Z轴排列任务

RESTART\_PACKAGES	-----------  该常量已过时  RestartPackage（String） API已不再支持

SEND\_SMS	-----------  允许应用发送SMS短信

SET\_ACTIVITY\_WATCHER	-----------  允许应用监视在系统中Activity是如何全局启动的

SET\_ALARM	-----------  允许应用通过广播Intent为用户设置提醒

SET\_ALWAYS\_FINISH	-----------  允许应用在处于后台时是否结束Activity

SET\_ANIMATION\_SCALE	-----------  修改全局动画缩放因子

SET\_DEBUG\_APP	-----------  配置应用进行调试

SET\_ORIENTATION	-----------  允许对屏幕方向（事实上就是旋转）设置的底层访问

SET\_POINTER\_SPEED	-----------  允许对指针速度设置的底层访问

SET\_PREFERRED\_APPLICATIONS	-----------  该常量已过时  详情参考 addPackageToPreferred（String）API

SET\_PROCESS\_LIMIT   -----------     许应用设置最大的（但不是必须的）运行进程数量

SET\_TIME	-----------  允许应用设置系统时间

SET\_TIME\_ZONE	-----------  允许应用设置系统时区

SET\_WALLPAPER	-----------  允许应用设置壁纸

SET\_WALLPAPER\_HINTS	-----------  允许应用设置壁纸提示

SIGNAL\_PERSISTENT\_PROCESSES	-----------  允许应用请求信号发送到所有显示的进程中

STATUS\_BAR	-----------  允许应用打开、关闭或禁用状态栏或图标

SUBSCRIBED\_FEEDS\_READ	-----------  允许应用程序访问订阅 Feed ContentProvider

SUBSCRIBED\_FEEDS\_WRITE	

SYSTEM\_ALERT\_WINDOW	-----------  允许一个程序打开使用TYPE\_SYS<input type="button"  />TEM\_ALERT的窗口，显示在其他所有程序之上

UPDATE\_DEVICE\_STATS	-----------  允许应用程序更新设备统计

USE\_CREDENTIALS	-----------  允许应用从AccountManager 请求 authtokens

USE\_SIP	-----------  允许应用程序使用SIP服务

VIBRATE	-----------  允许访问振动器

WAKE\_LOCK	-----------  允许使用PowerManager WakeLocks防止处理器休眠或屏幕变暗

WRITE\_APN\_SETTINGS	-----------  允许应用写入APN设置

WRITE\_CALENDAR	-----------  允许应用写入但不读取用户日历数据

WRITE\_CONTACKS	-----------  允许应用写入但不读取用户联系人数据

WRITE\_EXTERNAL\_STORAGE	-----------  允许应用写入到外部存储

WRITE\_GSERVICES	-----------  允许应用修改Google服务地图

WRITE\_HISTORY\_BOOKMARKS	-----------  允许应用写入（但不读取）用户的浏览历史和书签

WRITE\_SECURE\_SETTINGS	-----------  允许应用读写安全系统设置

WRITE\_SETTINGS	-----------  允许应用读写系统设置

WRITE\_SMS	-----------  允许应用写SMS信息
