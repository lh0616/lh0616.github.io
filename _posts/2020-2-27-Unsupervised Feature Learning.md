---
layout:     post
title:      Unsupervised Feature learning
subtitle:   Image Based
date:       2020-2-27
author:     Hohoo
header-img: img/desk2.jpg
catalog: true
tags:
    - Unsupervise
    - Paper Reading
    - deep learning
---


> Personal Paper Reading

## Introduction
&nbsp; &nbsp; In a recent program, I need to complete a Classification task, while supervised deep learning methods may not work because 
of the lack of labeled data. So I'd like to solve this probelm via unsupervised feature learning. This blog records some 
understanding of three popular relative works and some fragmented notes. 

New to this field, limited personal ablity, apology for any error.

## Abstract


## 查看你的系统有几种shell

	cat /etc/shells

显示

	/bin/bash
	/bin/csh
	/bin/ksh
	/bin/sh
	/bin/tcsh
	/bin/zsh
	
## 安装 oh my zsh

	git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
	cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

重新打开终端，输入 
	
	zsh

即可切换终端，并且发现 oh my zsh 已经帮我们配置好 zsh 了

## 修改主题

	open ~/.zshrc 
	
修改 `ZSH_THEME=”robbyrussell”`，主题在 ~/.oh-my-zsh/themes 目录下。
修改为

	ZSH_THEME="kolo"

可以[参照这里](https://github.com/robbyrussell/oh-my-zsh/wiki/themes)进行选择.

## 设置为默认shell

	chsh -s /bin/zsh
	
## 添加自定义命令

	open ~/.zshrc
添加显示隐藏文件的快捷命令

	alias fd='defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder'
	alias fh='defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder'