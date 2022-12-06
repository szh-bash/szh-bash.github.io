---
layout: default
title: ProjectArk
description: The best auxiliary program for Digimon Masters Online Global
projectArk: True
---

# Setup
> Version: v2.14
>
> Date: 2022.12.6

- [Setup](#setup)
  - [环境要求](#环境要求)
  - [安装与启动](#安装与启动)
  - [更新方式](#更新方式)
  - [快捷键](#快捷键)
  - [其他](#其他)

## 环境要求
- 操作系统：windows 11 21H2 及之前
- 系统缩放：100%
- 网络：流畅访问[官网](https://blog.immortal-s.asia)
- 硬盘：15 MB 及以上空间

## 安装与启动
- 下载并解压最新 projectArk 程序
- 运行 projectArk.exe，初次登陆设置软件 id 和 key 参数（账号密码请向作者索要）
  
      ...
      "id": "guest",
      "key": "guest",
      ...
- 网络要求：
  - 若遇到连接障碍，可尝试开/关全局代理、加速后再次启动 ark，成功启动后可随意开/关代理、加速器
  - 启动时建议不要将 127.0.0.1 转发至代理
- 启动画面：

  ![23](/projectArk/resource/init.png)

- 主界面：

  ![12](/projectArk/resource/main.png)

- 时长：

  ![12](/projectArk/resource/time.png)

## 更新方式
- [官网](https://blog.immortal-s.asia/projectArk/download)下载更新
- 检测到新版后右键托盘图标-Update

  ![12](/projectArk/resource/update_info.png)

  ![12](/projectArk/resource/update.png)

## 快捷键
<!-- - ctrl-e: 隐藏 projectArk 窗口 -->
- ctrl-w: 关闭 projectArk
- ctrl-s: 保存参数设置
- cfg.json 自定义快捷键位

      ...
      "ShortCut": {
          <!-- "hide": "E", -->
          "save": "S",
          "exit": "W"
      }
      ...

## 其他
- cfg.json 中均采用英文双引号，不可用单引号或中文双引号
