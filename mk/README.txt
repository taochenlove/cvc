/** @copyright (c) 2017, Shenzhen Forward Industry Co.Ltd. All Rights Reserved.
  * @author  huangjimin
  * @date 2017-09-26
  * @brief build infrastructure
  * 
  */
﻿
编译步骤：
 进到需要编译的目录
 如果是用户态库或者可执行文件
  make OVRT=xxxx， xxx是make help看到的选项之一
 如果是内核模块
 make OVRT=xxxx LINUX_KDIR=/path/to/linuxsrcdir
 
 
 
编译相关的说明
make help会列出所有支持的target

交叉编译linux内核模块需要指定
 OVRT或者TARGET
 CROSS_COMPLIE
 LINUX_KDIR

交叉编译linux用户态程序需要指定
 OVRT或者TARGET
 CROSS_COMPLIE


注意 大小端BE_HOST需要在plat.$(TARGET)指定对


编译阶段调试
#打印控制
 V=0 打印简短输出编译邻接信息
 V=1 打印完整输出编译、链接时的命令
 V=2 更进一步，打印链接时搜索路径
 V=3 更进一步，打印链接时搜索路径基础上打印链接lds
#预处理文件中间文件输出
 EEEE = 1是会将CC -E的 作为.i文件放在.o所在目录

#编译速度控制
 J=1
 J=4
 J=N 可根据编译机器CPU数量调整，加速编译


原理简介


加新的内核模块或者新的可执行程序
exec
kmod
LD_A_FILES
LD_O_FILES
LD_L_LISTS
LD_INFO_OPTS


加新的库
 库的.c文件分布在一个目录
 库的.c文件分布在多个目录
 
arm64be平台交叉编译

mips64 xlp平台交叉编译
 