---
title: 更新 Hexo 和插件、主题
date: 2023-1-4 20:36:04
categories: 
	- 教程
	- Hexo
tags: Hexo
description: 给你的 Hexo 更新 Hexo 版本、主题版本与插件以获取新版本功能或修复 bug
---

## 准备工作
备份好所有关于 Hexo 的文件，避免出错跑路（悲
以下所有操作建议在 Git 里运行
懒得配图了捏（））（

### 清理 npm 缓存
```Bash
npm cache clean -f --force
```

### 安装升级工具（全局）
```Bash
npm install -g npm-check
npm install -g npm-upgrade
```

## 更新 Hexo 版本

### 检查全局包是否可更新
```Bash 
npm-check -g
```

### 更新全局包
```Bash
npm update -g
```

### 更新 Hexo 版本
```Bash
npm install --global hexo
```

## 更新插件版本

### 更换目录至博客根目录
```Bash
cd /盘符/路径
# 比如我的在 D 盘下的 myblog/hexo
cd /d/myblog/hexo
```

### 检查可更新的包
```Bash
npm-check
```

### 更新 package.json 与插件
```Bash
npm-upgrade
npm update --save --force
```

### 删除模块目录与旧项目（可做）
```Bash
rm -rf node_modules && npm install --force
rm -rf .deploy_git --force
```

### 修复依赖（没问题就不做）
```Bash
npm audix
```

## 更新主题版本

### 切换到主题目录
```Bash
cd themes/主题名
# 比如我的主题是 butterfly
cd themes/butterfly
```

### 更新主题
```Bash
git add .
git stash
git pull
git stash pop
```

## 小结
最后重新 <code>hexo s</code> 或 <code>hexo cl&&hexo g&&hexo d</code> 就可以了捏