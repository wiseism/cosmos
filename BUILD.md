# Cosmos Lessons CMake 构建系统

## 概述

本项目使用CMake构建系统来编译Cosmos操作系统的各个课程项目。支持Ubuntu 24系统。

## 前置要求

- CMake 3.10或更高版本
- GCC编译器
- NASM汇编器（用于编译包含汇编代码的项目）
- Linux内核头文件（用于编译内核模块）

安装依赖：
```bash
sudo apt update
sudo apt install cmake gcc nasm linux-headers-$(uname -r)
```

## 使用方法

### 编译所有项目

```bash
mkdir build
cd build
cmake ..
make
```

### 选择性编译

只编译特定的课程：

```bash
mkdir build
cd build
cmake -DBUILD_LESSON01=ON -DBUILD_LESSON02=OFF ..
make
```

可用的编译选项：
- `BUILD_ALL`: 编译所有课程（默认：ON）
- `BUILD_LESSON01`: 编译lesson01
- `BUILD_LESSON02`: 编译lesson02
- `BUILD_LESSON10_11`: 编译lesson10~11
- `BUILD_LESSON12`: 编译lesson12
- `BUILD_LESSON13`: 编译lesson13
- `BUILD_LESSON16_18`: 编译lesson16~18
- `BUILD_LESSON19_21`: 编译lesson19~21
- `BUILD_LESSON24`: 编译lesson24
- `BUILD_LESSON25_26`: 编译lesson25~26
- `BUILD_LESSON28_29`: 编译lesson28~29
- `BUILD_LESSON30`: 编译lesson30
- `BUILD_LESSON31`: 编译lesson31
- `BUILD_LESSON32`: 编译lesson32
- `BUILD_LESSON33`: 编译lesson33
- `BUILD_LESSON34`: 编译lesson34
- `BUILD_LESSON35`: 编译lesson35
- `BUILD_LESSON37`: 编译lesson37
- `BUILD_LESSON41`: 编译lesson41
- `BUILD_LESSON41_1`: 编译lesson41.1
- `BUILD_LESSON41_2`: 编译lesson41.2
- `BUILD_LESSON41_3`: 编译lesson41.3(uefi)
- `BUILD_LESSON42`: 编译lesson42

### 清理构建

```bash
make clean
```

或删除整个构建目录：
```bash
cd ..
rm -rf build
```

## 项目说明

### 简单C程序
- **lesson01/HelloWorld**: Hello World程序
- **lesson42**: CPU信息查询程序

### 操作系统相关项目
- **lesson02/HelloOS**: 简单的操作系统引导程序
- **lesson10~11/Cosmos**: Cosmos操作系统引导加载器
- **lesson12~37/Cosmos**: Cosmos操作系统各个版本

### 内核模块
- **lesson31/misc**: 内核模块示例
- **lesson35**: 文件系统内核模块

注意：内核模块需要使用内核构建系统编译，CMake配置中会显示相应的提示信息。

## 编译输出

编译后的可执行文件和二进制文件会生成在build目录的相应子目录中。

## 注意事项

1. 某些Cosmos项目使用原始的Makefile构建系统，CMake会调用这些Makefile
2. 内核模块需要单独使用make命令编译
3. 某些项目可能需要特定的工具链或依赖

## 故障排除

如果遇到编译错误，请检查：
1. 是否安装了所有必需的依赖
2. CMake版本是否满足要求
3. 编译器版本是否兼容
4. 是否有足够的权限（某些操作可能需要sudo）
