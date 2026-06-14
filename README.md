# 校园网认证客户端

一个功能完善的校园网认证工具，支持自动登录、断网重连、VPN代理管理等功能。

## 功能特性

### 校园网认证
- ✅ 自动登录 - 启动软件后自动登录第一个账号
- ✅ 断网自动重连 - 每30秒检测网络状态，断网后自动重新认证
- ✅ 多账号管理 - 支持保存多个账号，快速切换
- ✅ 流量统计 - 实时显示上传/下载速率和累计流量
- ✅ 系统托盘 - 最化到托盘，后台运行不干扰

### VPN 代理面板
- ✅ FlClash 风格界面 - 左侧导航 + 多页面布局
- ✅ 代理节点管理 - 显示节点名称、类型、延迟
- ✅ 规则列表 - 查看分流规则，支持搜索过滤
- ✅ 连接监控 - 实时显示活跃连接
- ✅ 流量仪表盘 - 实时速率 + 累计统计 + 公网IP
- ✅ 配置导入 - 支持文件导入、URL下载
- ✅ 系统代理切换 - 一键开启/关闭系统代理
- ✅ 断网自动重连 - VPN断开后自动重启核心

### 其他特性
- ✅ 单实例运行 - 打开第二个程序时激活已有窗口
- ✅ 网络类型检测 - 自动识别有线/WiFi连接
- ✅ 速率测试 - 内置上传/下载速率测试

## 目录结构

```
小白便携UI升级版/
├── app/
│   ├── Dialer.jar          # 主程序
│   ├── config.ini          # 配置文件
│   ├── client.jar          # 认证核心
│   ├── jre/                # 内置JRE
│   ├── mihomo/             # VPN核心
│   │   ├── mihomo.exe      # Clash Meta 核心
│   │   └── config.yaml     # VPN配置
│   └── icon.png            # 程序图标
├── src/
│   └── FinalGUI.java       # 源代码
└── 启动.bat                # 启动脚本
```

## 使用方法

### 校园网认证
1. 运行 `启动.bat` 或直接运行 `app/Dialer.jar`
2. 输入校园网账号和密码
3. 点击"登录"按钮
4. 登录成功后会自动启动断网监控

### VPN 模式
1. 点击右上角"☁ VPN 模式"按钮切换到VPN面板
2. 点击"▶ 点击启动 VPN"启动代理
3. 在"配置"页面导入订阅链接或配置文件
4. 在"代理"页面查看节点列表，点击"测速"测试延迟
5. 在"数据"页面查看实时流量和公网IP

### 断网自动重连
- 校园网认证成功后自动启动监控
- 每30秒检测网络连通性
- 检测到断网后自动重新登录

## 技术实现

### 校园网认证
- 通过内置认证核心（client.jar）与校园网服务器通信
- 支持模拟器模式兼容不同网络环境

### VPN 核心
- 使用 [mihomo](https://github.com/MetaCubeX/mihomo) (Clash Meta) 作为代理核心
- 通过 REST API (端口 9090) 控制核心
- 支持规则/全局/直连三种模式切换

### 断网检测
- 访问 `test.ustc.edu.cn` 或 `baidu.com` 检测连通性
- VPN 模式通过 `/proxies` API 检测节点延迟

### 单实例机制
- 使用端口 52346 作为实例锁
- 第二个实例启动时发送激活信号到已有实例

## 配置说明

### config.ini
```
autoStart=true        # 开机自启动
autoLogin=true        # 自动登录
monitor=true          # 断网监控
speedMonitor=true     # 速率监控
```

### VPN 配置
- 配置文件位于 `app/mihomo/config.yaml`
- 支持标准 Clash 配置格式
- 通过"配置管理"页面导入订阅

## 系统要求

- Windows 7/10/11
- Java 8+ (内置 JRE)
- 网络连接（有线或WiFi）

## 开发信息

- 语言: Java (Swing GUI)
- 认证核心: 内置 client.jar
- VPN 核心: mihomo (Clash Meta)
- 界面风格: FlClash / Material Design

## 许可证

本项目仅供学习和个人使用。

## 致谢

- [mihomo](https://github.com/MetaCubeX/mihomo) - VPN 核心
- [FlClash](https://github.com/chen08209/FlClash) - UI 设计参考