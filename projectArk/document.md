---
layout: default
title: ProjectArk
description: The best auxiliary program for Digimon Masters Online Global
projectArk: True
---
# Document
> Version: v0.79
>
> Date: 2022.4.11
>
> Author: Immortal.S

## 环境要求
- 大漠插件：v7.2149
- 操作系统：windows 11 21H2 及之前
- 系统缩放：部分功能要求系统缩放 100%
- 网络：流畅访问 [szh-bash.github.io](https://szh-bash.github.io)
- 硬盘：15 MB 及以上空间

## 安装与启动
- 下载并解压最新 projectArk 压缩包
- 下载并解压最新大漠插件压缩包并注册 dm.dll 到系统
- 阅读使用手册，学习设置 set/cfg.json 参数
- 运行 projectArk.exe
- 启动画面：

  ![23](/projectArk/resource/init.png)

- 主界面：

  ![23](/projectArk/resource/main.png)

## 更新方式
- projectArk 启动时自动更新，保留参数设置
  - cfg.json

        ...
        "arkUpdateLater": "Y", 
        ...
        建议网络不好的用户将此项设置为 Y，程序将在启动后下载更新包避免网络波动导致下载意外中断更新出错，更新包下载完毕后提示更新；
        否则设置为 N，程序将在更新完毕后启动
- 群文件下载更新

## 快捷键
- ctrl-e: 隐藏 projectArk 窗口
- ctrl-w: 关闭 projectArk
- ctrl-s: 保存参数设置
- cfg.json 自定义快捷键位

      ...
      "ShortCut": {
          "hide": "E",
          "save": "S",
          "exit": "W"
      }
      ...

## 功能介绍

### Fast Initialize
- 建议仅勾选常用功能，加快 projectArk 程序启动速度
- 界面：

  ![12](/projectArk/resource/PreLoad.png)

### Hbu5
- 功能：自动扭蛋脚本，出货率约为 1 D-CodeII = 1 hbu5，自动断线重连
- 设置：

      - 填写 configure 页面中的账号、密码、二级密码（steam 用户无需填写）、客户端路径 (gdmo.exe) 信息并 save
      - 驯兽师的站位: 按“空格”可以与 D-Code II 扭蛋机对话
      - 游戏分辨率设置: 1024x768
      - 系统缩放设置: 100%
- 注意：
  - 此模式绑定的窗口将无视 hide 功能的优化设置，启用 hide 功能后将自动限制为 fps 上限 20 帧
  - 程序将仅绑定设置路径中的客户端窗口

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

### Kill - 支持全服
- 功能：杀死最顶层 DMO 窗口所在进程，可选择杀死仍处于加载保护盾阶段的 DMO 进程

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

     ![23](/projectArk/resource/hide.png)
    - hide: 是否隐藏 DMO 及其他窗口

          - 0，不启用隐藏功能
          - 1，启用隐藏功能
          - 2, 仅隐藏 DMO 进程中非客户端窗口，如启动时游戏盾 LOGO
    - cpu: 影响 rate 值意义 

          - 0, rate 值越大优化 CPU 占用效果越好
          - 1，rate 值代表 DMO 最大 fps 值
    - rate: 意义取决于 cpu 值
    
          - 非负整数，0 代表不优化 CPU 占用
    - 参数更新后重启 Hide 即可生效；点击 save 更新 set/cfg.json 文件内容
    - cfg.json["hide"~"downCpu"]
  - cfg.json 参数设置：隐藏非 DMO 窗口

        - cfg.json["hideWindow"]: [["进程名.exe", "窗口标题"，"窗口类型", 启用与否(1或0)], ["dats", "", "", 1]]
        - 数字 1 代表启用这条规则，0 则不启用
        - 窗口标题参数为模糊匹配，可填入目标窗口的部分标题，可省略
        - 窗口类型可省略
        - 具体可联系作者获取目标进程相关参数

### DATS
##### 说明
- 功能：通过持续监控 dats.exe 的挂机过程实现相应自动化功能，具体表现依据 DATS 页面参数设定。
- 参数:
  - cfg.json:

        ...
        "DATS":{
          ...
          "ExePath": "D:\\Game\\DigimonMasters\\DATS v5.91\\dats.exe",
          "Server-0": "国际服",
          "Mode": "野外" 
        }
        ...
      (若守护的是副本模式就把“野外”改为“副本”，第二行服务器同理)
- 使用：主界面单击 DATS 启用功能，去除勾选目标 dats.exe 的 “掉线重连” 并点击“开始”
- 注意：本功能运行期间 **不可用 Hide 功能隐藏 dats.exe 窗口**，目前只支持单个 dats.exe 挂机
- 界面：

  ![12](/projectArk/resource/DATS.png)
##### BSoDGuard
- 功能：防止 dats 断线重连时可能导致的电脑蓝屏问题
- **默认启用**

##### ReLogin - 仅支持单个弯刀脚本
- 功能：dats 崩溃后自动重启并挂机
- 参数设置：cfg["DATS"]["ExePath"] 字段设置 "dats.exe" 启动路径

##### NoACT
- 功能：DMO 登录后自动开启无动作

<!-- ##### HP
- 功能：检测到 dats 开始吃药后停止挂机，连续吃若干口药后继续挂机
- 使用说明：dats 设置较低的吃药血线，cfg["DATS"]["HP"]["key"] 为吃药键，["times"] 为吃药次数

##### DS
- 功能：数码兽 DS 耗尽后自动退化再进化，适用于小号挂野外
- 使用说明：DATS 设置数码兽回蓝按钮为非吃药键，例如攻击键 (默认为 1) -->

##### NoCD
- 功能：DMO 登录后自动开启无 CD 进化
- 注意：dats 挂机后会默认关闭无 CD 进化，本属性比较鸡肋

### Email
- 功能，点击 Email 按钮启用
  - 功能：连续登陆用户填写的账户，每个账户登录默认角色领取所有邮件并尝试领取顽固票后退出
  - 顽固票说明：需要将驯兽师挪到顽固兽 NPC 面前才可以自动领取顽骨副本票
  - cfg 字段

        - cfg.json["receiver"\]: [["账号"，"密码"，"二级密码"],["账号"，"密码"，"二级密码"]\]
        - 账户信息用中括号括起，账号间用逗号隔开
        - 必须用双引号
- 新功能**仍在开发中**
  - 界面：

    ![12](/projectArk/resource/Mail.png)
  - 功能说明

        - 核心功能：自动领取每日、特殊时段奖励，无需人为监管、不影响挂机账号，部分功能需要借用弯刀脚本
        - egg：领取指定天数百日蛋
        - mail：领取邮件
        - event：领取特殊时段在线奖励
        - ticket：领取门票，需要借用弯刀脚本-自动领票功能

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
  
### Login
- 功能
  - 启动 configure 路径记录的 gdmo.exe 并根据账号信息自动登录，路径请勿与 dats 负责路径重合，避免意外情况
  - 选区：奥米加服务器，可在服务器已满、服务器消失情况下自动登录。
  - 角色：上次登录的角色
- 字段
  - Configure 页面

    ![11](/projectArk/resource/login.png)

        - 从上往下依次是账号、密码、二级密码、启动路径
        - 启动路径示例：E:\GameKing\GDMO\GDMO.exe
        - 点击 show 可以显示密码明文，再点便恢复密文
        - 修改参数后重启功能立刻生效，点击 save 更新 set/cfg.json
        - steam 用户无需填写账号信息
  - cfg.json["userID"~"exePath"]
- 使用
  - 点击 login，自动绑定最顶层 dmo 窗口；若无已打开的 dmo 窗口则启动路径中的 dmo 程序
  - 若在待绑定的 dmo 窗口处于账号密码界面，请确保光标在账号栏保持跳动
- 用途：与 dats 多开不冲突，一般可用来启动仓库号摆商店，或上大号手动


## 其他
- 及时更新 dm.dll 版本避免意外 BUG
- cfg.json 中均采用英文双引号，不可用单引号或中文双引号
