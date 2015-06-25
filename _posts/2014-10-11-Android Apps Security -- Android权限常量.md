---
layout: post
title: Android Apps Security -- Android权限常量
---

ACCESS_CHECKIN_PROPERTIES   ----------   允许读写访问checkin数据库中的properties表，改值可以更新上传

ACCESS_COARSE_LOCATION	------------    允许程序访问Cell_ID或Wifi热点来获取粗略位置信息

ACCESS_FINE_LOCATION  ----------- 	允许程序访问精良位置（如GPS）

ACCESS_LOCATION_EXTRA_COMMANDS	 ---------   允许应用程序访问额外的位置服务命令

ACCESS_MOCK_LOCATION 	---------    允许程序创建模拟位置服务用于测试

ACCESS_NETWORK_STATE ---------	允许程序访问有关网络信息

ACCESS_SURFACE_FLINGER  --------    允许程序使用Surfaceflinger底层特性

ACCESS_WIFI_STATE	---------   允许程序访问wifi网络状态信息

ACCOUNT_MANAGER	 -----------    允许程序调用AccountAuthenticators

AUTHENTICATE_ACCOUNTS   ------------  允许应用作为AccountManager的AccountAuthenticator

BATTERY_STATES	 -------------    允许程序更新手机电池统计信息

BIND_APPWIDGET	-------------   允许应用程序告诉AppWidget的服务应用程序可以访问AppWidget的数据

BIND_DEVICE_ADMIN	------------  设备管理接收机是必须的，以确保只有系统可以与它进行交互

BIND_INPUT_METHOD	------------  InputMethodService是必须的，以确保只有系统可以绑定到它

BIND_REMOTEVIEWS	-----------   RemoteViewsService是必须的，以确保只有系统可以绑定到它

BIND_WALLPAPER	-----------   WallpaperService是必须的，以确保只有系统可以绑定到它

BLUETOOTH	-----------   允许引用连接到已配对的蓝牙设备

BLUETOOTH_ADMIN	-----------   允许应用发现和配对蓝牙设备

BRICK	-----------   请求能够禁用设备（非常危险）

BROADCAST_PACKAGE_REMOVED	-----------   允许应用在被移除后能收到广播通知

BROADCAST_SMS	-----------   允许应用能够广播SMS接收通知

BROADCAST_STICKY	-----------   允许应用广播Sticky Intent

BROADCAST_WAP_PUSH	-----------   允许应用程序广播一个WAP推-收通知

CALL_PHONE	-----------   允许应用发起一个电话，用户不用通过拨号用户界面，以确认被置于通话

CALL_PRIVILEGED	-----------   允许应用拨打任何号码，包含紧急号码，而无需通过拨号用户界面进行确认

CAMERA	-----------   请求访问使用照相设备

CHANGE_COMPONENT_ENABLE_STATE	-----------   允许一个应用改变另一个应用程序组件的启用状态（禁用或启用）

CHANGE_CONFIGURATION	-----------   允许应用修改当前设置，如本地化

CHANGE_NETWORK_STATE	-----------   允许应用改变网络连接状态

CHANGE_WIFI_MULTICAST_STATE	-----------   允许应用进入wifi多播模式

CHANGE_WIFI_STATE    -----------   	允许应用改变wifi连接状态

CLEAR_APP_CACHE	-----------  允许应用清除设备上所有已安装的应用程序缓存

CLEAR_APP_USER_DATA	-----------  允许应用清除用户数据

CONTROL_LOCATION_UPDATES	-----------  允许启用或禁止来自无线模块的位置更新提示

DELETE_CACHE_FILES	-----------  允许应用删除缓存文件

DELETE_PACKAGES	-----------  允许应用删除包

DEVICE_POWER	-----------  允许访问底层电源管理

DIAGNOSTIC  -----------  	允许应用RW诊断资源

DISABLE_KEYGUARD	-----------  允许应用禁用键盘锁

DUMP	-----------  允许应用检索系统服务的状态转储信息

EXPAND_STATUS_BAR	-----------  允许应用扩展或收缩在状态栏

FACTORY_TEST	-----------  允许作为一个工厂测试程序运行，以root用户运行

FLASHLIGHT	-----------  允许访问闪光灯

FORCE_BACK	-----------  允许应用强制执行返回操作，无论是否在顶层Activity

GET_ACCOUNTS	-----------  允许访问账户服务中的账户列表

GET_PACKAGE_SIZE	-----------  允许应用获取任何package占用空间容量

GET_TASKS	-----------  允许应用获取有关当前或最近运行的任务的信息：任务的缩略图表示、什么样的活动正在运行中等

GLOBAL_SEARCH	-----------  在Content Provider上使用该权限，能允许全局搜索系统来访问他们的数据

HARDWARE_TEST	-----------  允许访问硬件外设

INJECT_EVENTS	-----------  允许应用将用户时间注入时间流中（如按键、触摸及追踪球），并传递给任何窗口

INSTALL_LOCATION_PROVIDER	-----------  允许应用程序安装一个位置服务到位置管理器

INSTALL_PACKAGES	-----------  允许应用安装包文件

INTERNAL_SYSTEM_WINDOW	-----------  允许应用打开窗口，其作为系统用户界面部分使用

INTERNET	-----------  允许应用打开网络套接字

KILL_BACKGROUND_PROCESSES	-----------  允许应用调用 killBackgroundProcesses(String)

MANAGE_ACCOUNTS	-----------  允许应用管理AccountManager 中的账户

MANAGE_APP_TOKENS	-----------  允许应用管理窗口管理器中的应用令牌（如create、distory和Z-order）

MASTER_CLEAR	-----------  目前还没有明确的解释,Android开发网分析可能是清除一切数据,类似硬格机

MODIFY_AUDIO_SETTINGS	-----------  允许应用修改全局音频设置

MODIFY_PHONE_STATE	-----------  允许修改话机状态，如电源，人机接口等

MOUNT_FORMAT_FILESYSTEMS	-----------  允许格式化可移动存储设备的文件系统

MOUNT_UNMOUNT_FILESYSTEMS	-----------  允许安装和卸载可移动存储设备的文件系统

NFC	-----------  允许应用通过NFC执行IO操作

FERSISTENT_ACTIVITY	-----------  该常量已过时。此功能在未来将被删除，请不要使用。允许应用Activity持久

PROCESS_OUTGOING_CALLS	-----------  允许应用监视、修改或终止呼出

READ_CALENDAR	-----------  允许应用读取用户日历数据

READ_CONTACTS	-----------  允许应用读取用户联系人数据

READ_FRAME_BUFFER	-----------  允许应用进行屏幕截图和更多常规的访问帧缓冲数据

READ_HISTORY_BOOKMARKS	-----------  允许应用读取（但不能写入）用户浏览历史或书签

READ_INPUT_STATE	-----------  允许应用返回当前按键状态

READ_LOGS	-----------  允许应用读取底层系统日志文件

READ_PHONE_STATE	-----------  允许应用读取（不能写）手机状态

ERAD_SMS	-----------  允许应用读取短信

READ_SYNC_SETTINGS	-----------  允许应用读取同步设置

READ_SYNC_STATS	-----------  允许应用读取同步状态

REBOOT	-----------  重新启动设备必须要有此权限

RECEIVE_BOOT_COMPLETED	-----------  允许应用接收在系统完成启动后发出的ACTION_BOOT_COMPLETED广播

RECEIVE_MMS	-----------  允许应用监控将收到的MMS彩信，并作记录或处理

RECEIVE_SMS	-----------  允许应用监控将收到的SMS短信，并作记录或处理

RECEIVE_WAP_PUSH	-----------  允许应用监控将收到的WAP推送信息

RECORD_AUDIO	-----------  允许应用录制音频

REORDER_TASKS	-----------  允许应用改变Z轴排列任务

RESTART_PACKAGES	-----------  该常量已过时  RestartPackage（String） API已不再支持

SEND_SMS	-----------  允许应用发送SMS短信

SET_ACTIVITY_WATCHER	-----------  允许应用监视在系统中Activity是如何全局启动的

SET_ALARM	-----------  允许应用通过广播Intent为用户设置提醒

SET_ALWAYS_FINISH	-----------  允许应用在处于后台时是否结束Activity

SET_ANIMATION_SCALE	-----------  修改全局动画缩放因子

SET_DEBUG_APP	-----------  配置应用进行调试

SET_ORIENTATION	-----------  允许对屏幕方向（事实上就是旋转）设置的底层访问

SET_POINTER_SPEED	-----------  允许对指针速度设置的底层访问

SET_PREFERRED_APPLICATIONS	-----------  该常量已过时  详情参考 addPackageToPreferred（String）API

SET_PROCESS_LIMIT   -----------     许应用设置最大的（但不是必须的）运行进程数量

SET_TIME	-----------  允许应用设置系统时间

SET_TIME_ZONE	-----------  允许应用设置系统时区

SET_WALLPAPER	-----------  允许应用设置壁纸

SET_WALLPAPER_HINTS	-----------  允许应用设置壁纸提示

SIGNAL_PERSISTENT_PROCESSES	-----------  允许应用请求信号发送到所有显示的进程中

STATUS_BAR	-----------  允许应用打开、关闭或禁用状态栏或图标

SUBSCRIBED_FEEDS_READ	-----------  允许应用程序访问订阅 Feed ContentProvider

SUBSCRIBED_FEEDS_WRITE	

SYSTEM_ALERT_WINDOW	-----------  允许一个程序打开使用TYPE_SYSTEM_ALERT的窗口，显示在其他所有程序之上

UPDATE_DEVICE_STATS	-----------  允许应用程序更新设备统计

USE_CREDENTIALS	-----------  允许应用从AccountManager 请求 authtokens

USE_SIP	-----------  允许应用程序使用SIP服务

VIBRATE	-----------  允许访问振动器

WAKE_LOCK	-----------  允许使用PowerManager WakeLocks防止处理器休眠或屏幕变暗

WRITE_APN_SETTINGS	-----------  允许应用写入APN设置

WRITE_CALENDAR	-----------  允许应用写入但不读取用户日历数据

WRITE_CONTACKS	-----------  允许应用写入但不读取用户联系人数据

WRITE_EXTERNAL_STORAGE	-----------  允许应用写入到外部存储

WRITE_GSERVICES	-----------  允许应用修改Google服务地图

WRITE_HISTORY_BOOKMARKS	-----------  允许应用写入（但不读取）用户的浏览历史和书签

WRITE_SECURE_SETTINGS	-----------  允许应用读写安全系统设置

WRITE_SETTINGS	-----------  允许应用读写系统设置

WRITE_SMS	-----------  允许应用写SMS信息
