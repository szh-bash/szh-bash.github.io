---
layout: default
title: ProjectArk
description: The best auxiliary program for Digimon Masters Online Global
projectArk: True
---

# DMO
> Version: v2.14
>
> Date: 2022.12.6

- [DMO](#dmo)
    - [PreLoad](#preload)
    - [Hbu5](#hbu5)
    - [Colo](#colo)
    - [Kill - AllServer](#kill---allserver)
    - [Top - AllServer](#top---allserver)
    - [Hide - AllServer](#hide---allserver)
    - [DATS - AllServer](#dats---allserver)
        - [说明](#说明)
        - [BSoDGuard](#bsodguard)
        - [ReLogin - 仅支持单个弯刀脚本](#relogin---仅支持单个弯刀脚本)
        - [NoACT](#noact)
        - [Start](#start)
    - [Login](#login)
    - [Update](#update)
    - [Mail](#mail)
  - [其他](#其他)

### PreLoad
> 选择需要显示的标签页面

- 不勾选 RPG、DATS、Hide、Hbu5、Top 可以加快 projectArk 程序启动速度
- 界面：

  ![12](/projectArk/resource/PreLoad.png)

### Hbu5
- 功能：自动后台截胡 hbu5 ，出货率约为 1.2 D-Code II = 1 hbu5，支持断线重连
- 设置：

      - 填写 configure 页面中的账号、密码、二级密码（steam 用户无需填写）、客户端路径 (gdmo.exe) 信息并 save
      - 驯兽师的站位: 按“空格”可以与 D-Code II 扭蛋机对话，请确保 ark 可以自动打开扭蛋机并正确识别 HBU5 余量
      - 游戏分辨率设置: 1024x768
      - 系统缩放设置: 100%
- 注意：
  - 如果遇到不抽扭蛋的情况，可尝试将 cfg.json["fastHbu5"] 改为 0 再次尝试，若还是不行请联系作者
  - 启用 hide 功能后将无视用户设置，默认采用 cpu=1\|rate=20
  - 程序将仅绑定 configure 中设定的 gdmo_path 客户端程序

### Colo
- 功能：自动快速召唤 Colo 下一关，可在中途转为弯刀打怪，后两种打怪模式下角色可提前自动跑至下一层 BOSS 刷新点等待（需要正确设置当前层数），反馈每层击杀怪物时间以及总 Colo 时间
- 环境要求：系统缩放 100%
- 使用说明
  - 参数设置

        - mode
          - summon only: 仅召唤
          - attack only: 仅打怪
          - summon & attack: 召唤至指定层后转由 dats 打怪
        - start: 选择当前起始层
        - attack: 转为战斗的层数
        - 驯兽师自动召唤位置要求：按空格可以与 NPC 对话
  - 启动功能：点击 Colo 自动控制最顶层 DMO 窗口
  - 终止功能：再次点击 Colo
- 注意事项：使用前请关闭与 NPC 对话界面以及背包
- 界面：

  ![12](/projectArk/resource/Colo.png)

### Kill - AllServer
- 杀死最顶层 DMO 窗口所在进程，可选择杀死仍处于加载保护盾阶段的 DMO 进程
- 也可杀死 RPG 进程

### Top - AllServer
- 持续动态智能置顶非 DMO 窗口，在 dmo 弹窗后 0.3s 内切换为之前的顶层窗口

### Hide - AllServer
- 功能
  - 自动优化全部 DMO 窗口 CPU 占用，最低可降低至 **1%** 以下
  - 自动隐藏全部 DMO 窗口，包括启动阶段的奥米加图标
  - 自动隐藏指定非 DMO 窗口，如 DATS、vmware 等
  - 上述功能对断线重连的 DMO 窗口依然自动生效
    - 若 DATS 未被隐藏，projectArk 将在 DMO 被 DATS 绑定打怪后优化 CPU
    - 若 DATS 被隐藏，projectArk 将在 DMO 账号登录完成的 60 秒后优化 CPU
- 注意: 
  - CPU 具体优化与 CPU、游戏场景相关，**追 BOSS 时优化效果较差**
  - 不可在 DMO 窗口正在加载地图或登陆过程中开始启动此功能
- 使用：主页面单击 Hide 启用功能，具体表现依据 configure 页面参数以及 cfg.json 中参数设定
- DMO 相关功能字段
  - Configure 页面参数解释：隐藏功能及 DMO 优化

     ![23](/projectArk/resource/hide.png)
    - hide: 是否隐藏 DMO 及其他窗口

          0: 不启用隐藏功能
          1: 启用隐藏功能
          2: 仅隐藏 DMO 进程中非客户端窗口，如启动时游戏盾 LOGO
    - cpu: 影响 rate 值意义 

          0: rate 值越大优化 CPU 占用效果越好
          1: rate 值代表 DMO 最大 fps 值
    - rate: 意义取决于 cpu 值
    
          - 非负整数，0 代表不优化 CPU 占用
          - 未被弯刀或 projectArk(login|hbu5) 绑定的 DMO 窗口默认采用 cpu=1|rate=1
          - hbu5 绑定的窗口默认采用 cpu=1|rate=20
    - 参数更新后重启 Hide 即可生效；点击 save 更新 set/cfg.json 文件内容
    - cfg.json["hide"~"downCpu"]
  - cfg.json 参数设置：隐藏非 DMO 窗口

        - cfg.json["hideWindow"]: [["进程名.exe", "窗口标题"，"窗口类型", 启用与否(1或0)], ["dats", "", "", 1]]
        - 数字 1 代表启用这条规则，0 则不启用
        - 窗口标题参数为模糊匹配，可填入目标窗口的部分标题，可省略
        - 窗口类型可省略
        - 具体可联系作者获取目标进程相关参数

### DATS - AllServer
##### 说明
> 通过持续监控弯刀挂机过程实现相应自动化功能，具体表现依据 DATS 页面参数设定。

- 参数：Config 页面设置 dats.exe 启动路径；DATS 页面设置服务器、挂机模式
- 使用：
  - 取消勾选弯刀“掉线重连”再点击“开始”挂机
  - 主界面单击 DATS 启用功能
- 注意：
  - 停止弯刀时，**保持弯刀处于日志界面**，确保游戏**未处在地图加载界面**，点击弯刀“停止”按钮然后等待，直到 ark **日志显示 "dats stopped"** 再进行其他操作
  - 本功能运行期间不可用 Hide 功能隐藏弯刀窗口
  - 只支持守护单个弯刀脚本 
- 界面：

  ![12](/projectArk/resource/DATS.png)

##### BSoDGuard
- 防止 dats 断线重连时可能导致的电脑蓝屏问题
- **默认启用**

##### ReLogin - 仅支持单个弯刀脚本
- dats 崩溃后自动重启并挂机

##### NoACT
- DMO 登录后自动开启无动作

##### Start
- 若 PC 无 dats 进程则自动登录 dats 并开始挂机

<!-- ##### HP
- 功能：检测到 dats 开始吃药后停止挂机，连续吃若干口药后继续挂机
- 使用说明：dats 设置较低的吃药血线，cfg["DATS"]["HP"]["key"] 为吃药键，["times"] 为吃药次数

##### DS
- 功能：数码兽 DS 耗尽后自动退化再进化，适用于小号挂野外
- 使用说明：DATS 设置数码兽回蓝按钮为非吃药键，例如攻击键 (默认为 1) -->

<!-- ##### NoCD
- 功能：DMO 登录后自动开启无 CD 进化
- 注意：dats 挂机后会默认关闭无 CD 进化，本属性比较鸡肋 -->

### Login
- 功能
  - 启动 configure 路径记录的 gdmo.exe 并根据账号信息自动登录，根据 "KeepALive" 参数值决定是否保持角色在线（"Y" 或 "N"）
  - 选区：奥米加服务器，可在服务器已满、服务器消失情况下自动登录。
  - 角色：上次登录的角色
  - 注意：路径请勿与 dats 负责路径重合
- 字段
  - Configure 页面

    ![11](/projectArk/resource/login.png)

        - 从上往下依次是账号、密码、二级密码、启动路径
        - 启动路径示例：E:\GameKing\GDMO\GDMO.exe
        - 点击 show 可以显示密码明文，再点便恢复密文
        - 修改参数后重启功能立刻生效，点击 save 更新 set/cfg.json
        - steam 用户无需填写账号信息
  - cfg.json

        ...
        "userID": "账号",
        "pwd": "密码",
        "secPwd": "二级密码",
        "exePath": "E:\\GameKing\\GDMO\\GDMO.exe",
        "KeepALive": "Y" 代表启用保持在线，"N" 则关闭该功能
        ...
- 使用
  - 点击 login，自动绑定最顶层 dmo 窗口；若无已打开的 dmo 窗口则启动路径中的 dmo 程序
  - 若在待绑定的 dmo 窗口处于账号密码界面，请确保光标在账号栏保持跳动
- 用途：与 dats 多开不冲突，一般可用来启动仓库号摆商店，或上大号手动

### Update
- 功能： 一键搜索并更新路径中的全部 DMLauncher.exe 并退出
- 字段说明
  - cfg.json

        ...
        "updatePath":["E:/GameKing/GDMO/DMLauncher.exe",
                      "E:/GameKing"] 
        ...
  - 路径用双引号括起，逗号隔开相邻路径
  - '/' 或 '\\\\'划分客户端路径，不可用反斜杠 '\\'
  
### Mail
- 界面：

  ![12](/projectArk/resource/Mail.png)
- 核心功能：
  - 后台批量登陆账号，自动领取邮件、活动登录奖励等
  - 支持空号自动创建一个随机ID、随机角色、随机数码兽
  - 支持新角色自动做新手任务（需要借助未在挂机的弯刀脚本，自动任务选上“横滨镇”）
  - 自动记录各账号领取与否的状态
- 功能说明

      - mail：领取邮件
      - event：领取活动登陆奖励
      - expansion: 自动使用背包扩展（完成新手任务后会送 21 个）
      - reset: 重置各账号的领取状态
      - save: 保存选择的功能列表
- 账号信息
  - excel 打开 set 文件夹下的 account.csv 文件，按照示例填写账号信息
  - 示例：
  ![12](/projectArk/resource/account.png)
- 使用方法：
  - 填写账号信息
  - 勾选需要执行的功能
  - 点击主页面 Mail 按钮启动/停止
  - 停止后再次点击启动会从上次操作的账号开始
- 限制：
  - 仅限国际服奥米加区（GDMO-Omegamon）
  - 自动领取邮件的角色需要完成新手任务
  
## 其他
- cfg.json 中均采用英文双引号，不可用单引号或中文双引号