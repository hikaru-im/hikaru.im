---
title: Conda常用命令整理
published: 2025-03-10
description: ''
image: ''
tags: [ Conda, 环境管理, Python ]
category: 学习笔记
lang: ''
---

## Conda

一个开源的软件包管理系统和环境管理系统，主要用于解决Python开发中的依赖管理和多版本环境隔离问题，也支持其他编程语言。

### 创建 Conda 环境

```shell
conda create -n <env-name>
# Example
conda create -n fast3r python=3.11 cmake=3.14.0
```

### 激活 Conda 环境

```shell
conda activate <env-name>
```

### 列出 Conda 环境

```shell
conda info --envs
```

### 停用 Conda 环境

```shell
conda deactivate
```

### 删除环境

```shell
conda remove --name <env-name> --all
```

### 禁用 SSL 验证

```shell
conda config --set ssl_verify False
```

### 自定义环境和包缓存位置

```shell
envs_dirs:
  - /nfs/volume/user/conda_envs
pkgs_dirs:
  - /nfs/volume/user/conda_pkgs
```
