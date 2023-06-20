---
layout: default
title: ProjectArk
description: The best auxiliary program for DMO & DigimonRPG
projectArk: True
---

# Setup
> Version: v3.00
>
> Date: 2023.6.20

- [Setup](#setup)
  - [环境要求](#环境要求)
  - [安装与启动](#安装与启动)
  - [更新](#更新)
  - [选择配置](#选择配置)
  - [快捷键](#快捷键)
  - [其他](#其他)

## 环境要求
- 操作系统：windows 11 22H2 及之前
- 系统缩放：**100%**
- 网络：流畅访问[官网](https://blog.immortal-s.asia)
- 硬盘：25 MB 及以上空间
- 防火墙：添加**信任/白名单**

## 安装与启动
- 下载并解压最新 projectArk 程序
- 登录界面：
  - Safe: 安全模式，若需要兼容弯刀挂机则不勾选
  - Guard1/2: 护盾1/2，需要关闭 Secure Boot，无法启动或蓝屏则不勾选
  - 注：Safe 模式本身已足够安全，Guard仅为皆为锦上添花
  
  ![23](/projectArk/resource/ark_login.png)
- 启动画面：
  - 若启动时长时间停留在启动画面，可尝试开/关全局代理、加速后再次启动 ark，成功启动后可随意开/关代理、加速器
  
  ![23](/projectArk/resource/init.png)

- 主界面：

  ![12](/projectArk/resource/main.png)

- 时长：

  ![12](/projectArk/resource/time.png)

## 更新
- [官网](https://blog.immortal-s.asia/projectArk/download)下载更新
- 检测到新版后右键托盘图标-Update

  ![12](/projectArk/resource/update_info.png)

  ![12](/projectArk/resource/update.png)

## 选择配置
- 右键图标-set-选择配置

  ![12](/projectArk//resource/set.png)

## 快捷键
<!-- - ctrl-e: 隐藏 projectArk 窗口 -->
- ctrl-w: 关闭 projectArk
- ctrl-s: 保存参数设置
- cfg.json 自定义快捷键位

      ...
      "ShortCut": {
          "save": "S",
          "exit": "W"
      }
      ...

## 其他
- cfg.json 中均采用英文双引号，不可用单引号或中文双引号
