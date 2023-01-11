---
layout: default
title: ProjectArk
description: The best auxiliary program for DigimonRPG
projectArk: True
---

# RPG
> Version: v2.54
>
> Date: 2023.1.8

- [RPG](#rpg)
  - [界面](#界面)
  - [功能介绍](#功能介绍)
  - [其他](#其他)

## 界面
- 界面设置：

  ![12](/projectArk/resource/rpg_load.png)

- 时长：RPG 后为到期时间

  ![12](/projectArk/resource/time.png)
  
- 主界面：

  ![12](/projectArk/resource/RPG.png)


## 功能介绍
> 以下功能均支持后台

- roll: 自动打开转盘抽奖
- digimon: 
  - 野外自动识别的数码兽，不受等级、类别影响
  - "#Maze-Random-Run" 为迷宫随机跑模式，注意事先将人物移动至远离传送门
  - **支持全服**
- detect: 野外向识别到的数码兽自动发起对战；手刷列表外数码兽时**建议关闭此功能**可以大幅提升对战识别效率
- card: 自动刷卡
  - off: 不上卡
  - on: 自动上卡
  - auto: 自动上卡，用完后**从主背包自动补卡**，使用相同的卡片进行补充若背包中没有则不补卡。支持中途手动换卡，不需要重新点 run
  - cfg.json 设置使用的卡片槽
      
        ...
        "RPG":{
            ...
            "card":{
                "on":1,
                "key":"123" // 用背包卡槽123的卡；"456"就是用卡槽456的卡
            }
            ...
        }
- summon: 自动召唤
  - 1-单招
  - 2:once-模式队长只召唤一次，利用第二只宠召唤第三只宠使队长提前一回合出手
  - 2:twice-模式队长连招两只宠，带练两只低级满速数码兽时建议用此模式
  - slot: 召唤槽
    - slot0: 第一次召唤槽或单招
    - slot1: 第二次召唤槽
- evolve: 队长自动进化；死亡也后可自动进化。**进化阶段设置错误会导致不打怪**
- catch: 自动捕捉
  - 1hp 模式要求将一血卡放至卡槽1，且 card 调为 off
- battle
  - enemy: 最大怪物数量，0 则对战中**不攻击**
  - skill: 队长攻击技能
- evp: 主兽 evp < 25% 吃药
  - 下拉菜单选择药品种类
  - cfg.json 设置单次吃药个数
    
        ...
        "RPG":{
          ...
          "evp":{
              "type": 1,
              "times": 4 （代表一次吃4瓶evp药）
          }
          ...
        }
- item: 自动捡物，背包满后自动不捡
  - 选定捡模式："specific" ，拾取 select item 中勾选的道具
    - 右键托盘栏图标-select item-勾选道具
    - configure 中 RPG-item 字段直接设置捡(1)/不捡(0)
  - 单捡模式：选择列表中的具体道具
  - 不捡：none
  - 注意事项：不同玩家由于显示器参数不同可能会导致游戏内字体形状差异，出现列表中物品无法拾取情况请咨询作者
- exchange: Event 频道自动兑换材料及兑换速度
  - 道具标号：兑换聊天框中目标道具的标号，其中 "x1" 代表一倍速（单纯指鼠标左键间隔，并非加速挂）
  - 兑换次数：不解释
- lock: 键鼠锁定模式，避免误触
  - none: 不锁定
  - both: 键鼠均锁定
  - mouse: 仅锁定鼠标
  - keyboard: 仅锁定键盘
  - enemy 设为 0 则**不锁定**
- 保存配置：点击 save 按钮或组合键 ctrl-s


## 其他
- cfg.json 中均采用英文双引号，不可用单引号或中文双引号
