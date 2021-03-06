# 使用手册
> Description: The best auxiliary program for Digimon Masters Online (Global)
> 
> Author: Immortal.S 
> 
> Version: v0.54
>
> Date: 10.Feb.2022

## 环境要求
- 大漠插件：v7.2149
- 操作系统：windows 10 21H2 及之前
- 系统缩放：部分功能要求系统缩放 100%
- 硬盘: 20 MB 及以上空间
- 网络：连接互联网

## 安装与启动
- 下载并解压最新 projectArk 压缩包
- 下载并解压最新大漠插件压缩包并注册 dm.dll 到系统
- 阅读使用手册，学习设置 set/cfg.json 参数
- 运行 projectArk.exe
- 主界面：
  <!--  -->
  <!-- ![23](projectArk-readme/main.png) -->
  
  <img src="./projectArk-readme/main.png" height = "23%" width = "23%" alt="图片名称" align=center />
### 快捷启动
- 取消不常用功能预加载过程，加快 projectArk 程序启动速度
- 界面：

  ![12](projectArk-readme/PreLoad.png)

## 功能介绍

### Colo
- 功能：自动快速召唤 Colo 下一关，可在中途转为弯刀打怪，打怪模式下可提前跑至下一层 BOSS 刷新点等待，可反馈每层击杀怪物时间以及总 Colo 时间
- 环境要求：系统缩放 100%
- 使用说明
  - 参数设置
    - mode
      - summon only: 仅召唤
      - attack only: 仅打怪
      - summon & attack: 召唤至指定层后转由 dats 打怪
    - start: 选择当前起始层
    - attack: 转为战斗的层数
    - 驯兽师位置要求：按空格可以与 NPC 对话
  - 启动功能：点击 Colo 自动控制最顶层 DMO 窗口
  - 终止功能：再次点击 Colo
- 注意事项：使用前请关闭与 NPC 对话界面以及背包
- 界面：

  ![12](projectArk-readme/Colo.png)

### Kill
- 功能：点击后完全退出最顶层 GDMO 窗口所在进程

### Top - 支持全服
- 功能：持续动态智能置顶非 DMO 窗口，在 dmo 弹窗后 0.3s 内切换为之前正在阅读的窗口

### Hide - 支持全服
- 功能
  - 自动优化全部 DMO 窗口 CPU 占用，最低可降低至 **1%** 以下
  - 自动隐藏全部 DMO 窗口，包括启动阶段的奥米加图标
  - 自动隐藏指定非 DMO 窗口，如 DATS、vmware 等
  - 上述功能对断线重连的 DMO 窗口依然自动生效
    - 若 DATS 未被隐藏，projectArk 将在 DMO 被 DATS 绑定打怪后优化 CPU
    - 若 DATS 被隐藏，projectArk 将在 DMO 账号登录完成的 60 秒后优化 CPU
- 注意: 不可在 DMO 窗口正在加载地图或登陆过程中开始启动此功能
- 使用：主页面单击 Hide 启用功能，具体表现依据 configure 页面参数以及 cfg.json 中参数设定
- DMO 相关功能字段
  - Configure 页面参数解释：隐藏功能及 DMO 优化

     ![23](projectArk-readme/hide.png)
    - hide: 是否隐藏 DMO 及其他窗口
      - 0，不启用隐藏功能
      - 1，启用隐藏功能
    - cpu: 影响 rate 值意义 
      - 0, rate 值越大优化 CPU 占用效果越好
      - 1，rate 值代表 DMO 最大 fps 值
    - rate: 意义取决于 cpu 值
      - 非负整数，0 代表不优化 CPU 占用
    - 参数更新后主页面重开 Hide 即可生效；点击 save 更新 set/cfg.json 文件内容
    - cfg.json["hide"~"downCpu"]
  - cfg.json 参数设置：隐藏非 DMO 窗口
    - cfg.json["hideWindow"]: [["进程名.exe", "窗口标题"，"窗口类型"], ["dats", "", ""]\]
    - 窗口标题参数为模糊匹配，可填入目标窗口的部分标题，可省略
    - 窗口类型可省略
    - 具体可联系作者获取目标进程相关参数

### DATS - 即将支持全服
##### 说明
- 功能：通过 dats.exe 实现部分自动化功能，具体表现依据 DATS 页面参数设定。
- 使用：主界面单击 DATS 启用功能，去除勾选 dats.exe 的 “掉线重连” 并开始挂机
- 注意：本功能运行期间不可用 Hide 功能隐藏 dats.exe 窗口，目前只支持单个 dats.exe 挂机
- 界面：

  ![12](projectArk-readme/DATS.png)
##### BSoDGuard
- 功能：防止 dats 断线重连时可能导致的电脑蓝屏问题
- **默认启用**

##### NoACT
- 功能：DMO 登录后自动开启无动作

##### HP
- 功能：检测到 dats 开始吃药后停止挂机，连续吃若干口药后继续挂机
- 使用说明：dats 设置较低的吃药血线，cfg["DATS"]["HP"]["key"] 为吃药键，["times"] 为吃药次数

##### DS
- 功能：数码兽 DS 耗尽后自动退化再进化，适用于小号挂野外
- 使用说明：DATS 设置数码兽回蓝按钮为非吃药键，例如攻击键 (默认为 1)

##### ReLogin
- 功能：dats 崩溃后自动重启并挂机
- 参数设置：cfg["DATS"]["ExePath"] 字段设置 "dats.exe" 启动路径

##### NoCD
- 功能：DMO 登录后自动开启无 CD 进化
- 注意：dats 挂机后会默认关闭无 CD 进化，本属性比较鸡肋

### Email
- 旧功能，点击 Email 按钮启用
  - 功能：连续登陆用户填写的账户，每个账户登录默认角色领取所有邮件并尝试领取顽固票后退出
  - cfg 字段
    - cfg.json["receiver"\]: [["账号"，"密码"，"二级密码"],["账号"，"密码"，"二级密码"]\]
    - 账户信息用中括号括起，账号间用逗号隔开
    - 必须用双引号
  - 领顽固票说明：需要将驯兽师挪到顽固兽 NPC 面前才可以自动领取顽骨副本票
- 新功能，仍在开发中
  - 功能说明
    - 核心功能：自动领取每日、特殊时段奖励，无需人为监管、不影响挂机账号，部分功能需要借用弯刀脚本
    - egg：领取指定天数百日蛋
    - mail：领取邮件
    - event：领取特殊时段在线奖励
    - ticket：领取门票，需要借用弯刀脚本-自动领票功能
  - 界面：

    ![12](projectArk-readme/Mail.png)

### Update
- 功能： 一键更新路径中 DMLauncher.exe 并退出
- 字段说明
  - cfg.json["updatePath"] ：["E:/GameKing/GDMOa","E:/GameKing/GDMOb"] 
  - 路径用双引号括起，逗号隔开相邻路径
  - '/' 或 '\\\\'划分客户端路径，不可用反斜杠 '\\'
  
### Login
- 功能
  - 启动 configure 路径记录的 gdmo.exe 并根据账号信息自动登录，路径请勿与 dats 负责路径重合，避免意外情况
  - 选区：奥米加服务器，可在服务器已满、服务器消失情况下自动登录。
  - 角色：上次登录的角色
- 字段
  - Configure 页面
    - ![11](projectArk-readme/login.png)
    - 从上往下依次是账号、密码、二级密码、启动路径
    - 启动路径示例：E:\GameKing\GDMO\GDMO.exe
    - 点击 show 可以显示密码明文，再点便恢复密文
    - 修改参数后重启功能立刻生效，点击 save 更新 set/cfg.json
  - cfg.json["userID"~"exePath"]
- 使用
  - 打开新的 gdmo 窗口流程:
    - 点击 auto_login
    - 不要再切换到其他 DMO 窗口
  - 登录已打开的 gdmo 窗口流程:
    - 点击 auto_login
    - 2s 内点击待登录的 DMO 窗口，任意登录阶段均可
    - 若在输账号界面，请确保光标在账号栏保持跳动
  - 终止方式
    - 再次点击 auto_login
- 用途：与 dats 多开不冲突，一般可用来启动仓库号摆商店，或上大号手动

### Hbu5 - 暂不开放
- 功能：自动扭蛋脚本，鉴于用户使用策略会极大破坏整体玩家游戏社区体验，下次一定

## 其他
- 及时更新 dm.dll 版本避免意外 BUG
- cfg.json 中均采用英文双引号，不可用单引号或中文双引号
- 请于月初自觉缴纳当月服务器费用 5 元/机器，避免作者 **倒贴** 给大家用，谢谢合作
