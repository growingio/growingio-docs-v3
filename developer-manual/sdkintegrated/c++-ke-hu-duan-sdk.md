# C++ 客户端SDK

## **1 概述**

C++ 埋点 SDK 是用于记录 PC 端埋点的，例如在 MFC，.NET, Qt 程序中集成，以收集用户在程序界面上的操作。

采集流程：初始化 -> 埋点采集数据 -> Flush() 上报数据

进程退出时，若内存中仍有未 Flush 发送到服务端的数据，则会将数据保存到指定的暂存文件里，下次 Flush 时会从文件加载一起发送。可以通过参数调整最多暂存的数据条数，若未发送的数据条数超过该值，则从最早的数据开始淘汰。

## **2 集成SDK**

GIO SDK 提供两种集成方式可供选择 ① 源码集成 ② 动态库集成

### **2.1 源码集成**

&#x20;源码地址: https://github.com/growingio/growingio-sdk-windows-track/tree/master/manual\_track​

首先 GIO SDK 使用了 curl 库用于网络请求；您需要先配置支持 https 协议的 libcurl 于项目中 curl 源码：https://curl.se/download.html​

1.使用 VS2010 开发人员命令提示重新编译curl，进入到 curl 的 winbuild 的目录下使用 cmake 工具编译

完整命令行如下：&#x20;

nmake /f Makefile.vc mode=dll MACHINE=x64 //MACHINE=x64编译64位版本默认x86&#x20;

2.在 C/C++ ->常规 -> 附加包含目录->添加curl 目录 builds 下的 libcurl-vc10-x86-release-static-ipv6-sspi-winssl\include

3.链接器 -> 常规 -> 附加库目录 ->添加 curl 目录 builds 下 builds\libcurl-vc10-x86-release-static-ipv6-sspi-winssl\lib

4.链接器 -> 输入 -> 附加依赖项，添加 libcurl.lib;Ws2\_32.lib; Wldap32.lib; winmm.lib; Crypt32.lib;

5.在 C/C++ -> 预处理器 -> 预处理器定义中，加入 CURL\_STATICLIB 注：debug 与 release 配置相对于的库 将 manual\_track.h manual\_track.cpp 添加到项目引入头文件中即可使用

### **2.2 动态库集成**

&#x20;动态库地址:https://github.com/growingio/growingio-sdk-windows-track/tree/master/DLL​

以 vs2010 为例：

1.在 C/C++ ->常规 -> 附加包含目录->添加 manual\_track.h

2.链接器 -> 常规 -> 附加库目录 ->添加 manual\_track.lib所在目录

3.链接器 -> 输入 -> 附加依赖项，添加 manual\_track.lib

4.将 manual\_track.dll libcurl.dll复制到工作目录（exe所在目录下）

## **3 初始化SDK**

建议在主线程中初始化 SDK 生成单例对象

```
// 初始化 SDK 
// projectid: 项目id 
//domain 包名唯一标识该应用 
static bool Init(const string &projectid, string domain);
```

## **4 结束采集**

程序结束前务必调用Shutdown()结束SDK采集数据，否则可能存在数据丢失问题&#x20;

```
// 析构 SDK 实例，回到 Init 前的状态，未发送的数据将暂存到磁盘 
static void Shutdown();
```

## **5 埋点接口**

### **5.1设置属性**

```
void SetNumber(const string &property_name, int32_t value);
​
void SetNumber(const string &property_name, int64_t value);
​
void SetNumber(const string &property_name, double value);
​
void SetString(const string &property_name, const string &value);
​
void SetString(const string &property_name, const char *value);
​
void SetBool(const string &property_name, bool value);
​
void SetList(const string &property_name, const std::vector<string> &value);
​
void SetDateTime(const string &property_name, time_t seconds, int milliseconds);
​
// 字符串格式需要是: 2018-09-07 16:30:22.567
void SetDateTime(const string &property_name, const string &value);
growingio提供growingio_track::PropertiesNode类如上接口设置埋点事件属性，调用示例如：

growingio_track::PropertiesNode event_properties;
event_properties.SetString("computer_name", "ABCXYZ");
event_properties.SetNumber("test_number_int", 3);
event_properties.SetNumber("test_number_double", 3.14);
event_properties.SetBool("test_bool", true);
std::string test_string = "测试字符串";
event_properties.SetString("test_stl_string", test_string);
event_properties.SetDateTime("test_time", time(NULL), 0);
std::vector<std::string> test_list;
test_list.push_back("item1");
test_list.push_back("item2");
event_properties.SetList("test_list", test_list);
growingio_track::Sdk::Track("OpenApp", event_properties);
```

### **5.2 埋点接口**

```
//发送自定义事件 API cstm event_name 仅支持大小写字母,数字,_
static void Track(const string &event_name);
​
static void Track(const string &event_name, const PropertiesNode &properties);
​
//发送用户变量 API ppl
static void SetPeopleVariable(const PropertiesNode &properties);
​
//访问用户变量 API vstr
static void SetVisitor(const PropertiesNode &properties);
​
//转化变量 API evar
static void SetEvar(const PropertiesNode &properties);
```

### **5.3 登录id**

```
// 设置登录用户ID API
static void SetUserId(string userid);
​
// 清除登录用户ID API
static void ClearUserId();
```

## **6 上报数据**

将数据通过网络发送到服务端需要在代码适当的位置显式调用 Flush() 函数，将数据发送到服务端需要有可用的网络连接，建议在适当的位置调用，如后台线程，避免阻塞界面操作等。

```
// 将所有本地数据发送到服务端
static bool Flush();
​
// 触发一次发送，发送最多 part_size 条数据
// 当 drop_failed_record 为 true 时，发送失败则丢弃这些数据不再发送
// 当 drop_failed_record 为 false 时，发送失败仍保留在队列里，下次再试
static bool FlushPart(size_t part_size, bool drop_failed_record);
```

## **7 API汇总**

```
 // 初始化 SDK
 // projectid: 项目id
 //domain 包名唯一标识该应用
 static bool Init(const string &projectid,
				           string domain);
 //日志开关 默认false打开日志开关后，日志输出到c:\\asia_log\\下
 static void EnableLog(bool enable);
​
 // 将所有本地数据发送到服务端
 static bool Flush();
​
 // 触发一次发送，发送最多 part_size 条数据
 // 当 drop_failed_record 为 true 时，发送失败则丢弃这些数据不再发送
 // 当 drop_failed_record 为 false 时，发送失败仍保留在队列里，下次再试
 static bool FlushPart(size_t part_size, bool drop_failed_record);
​
 // 清空本地发送队列，包括内存和文件
 static void ClearQueue();
​
 // 析构 SDK 实例，回到 Init 前的状态，未发送的数据将暂存到磁盘
 static void Shutdown();
​
 //发送自定义事件 API cstm
 static void Track(const string &event_name);
​
 static void Track(const string &event_name, const PropertiesNode &properties);
​
 //发送用户变量 API ppl
 static void SetPeopleVariable(const PropertiesNode &properties);
​
 //访问用户变量 API vstr
 static void SetVisitor(const PropertiesNode &properties);
 //转化变量 API evar
 static void SetEvar(const PropertiesNode &properties);
​
 // 设置登录用户ID API
 static void SetUserId(string userid);
​
 https://gta.growingio.com/v5/projects/0a1b4118dd954ec3bcc69da5138bdb96/chartdata
​
 // clear登录用户ID API
 static void ClearUserId();
​
 // 使用追加的方式把队列中数据添加到本地文件中，默认是 false
 static void AppendRecordsToDisk(bool enable);
​
 // 将队列中的所有数据直接追加到本地文件中，并清空队列内容
 // 只有当开启 AppendRecordsToDisk 时调用此接口才有效
 static void DumpAllRecordsToDisk();
```

## 8 对于 .NET的支持

C++SDK 提供C++/CLI版本动态库以支持[.](http://xn--6kqx04a.net)NET程序的埋点数据采集，你需要如下操作：

1.添加引用 manualtrackCliDll.dll

2.将对应版本的 manualtrack.dll libcurl.dll 复制到工作目录
