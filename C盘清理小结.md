## C盘清理小结

**可视化占用软件：SpaceSniffer**

​	[GitHub开源仓库](https://github.com/redtrillix/SpaceSniffer)，[下载地址](https://github.com/redtrillix/SpaceSniffer/releases)

### 1. Windows通用部分

#### Windows自带的磁盘清理功能

- 介绍：Windows自带的磁盘清理功能，可以清理临时文件和Windows升级残留等

- 可能的危险：无

- 清理方法：

  1. 在Windows搜索框中输入“磁盘清理”，点击打开

  2. 选择要清理的磁盘（一般为C盘），点击确定

  3. 在弹出的窗口中，选择要清理的文件类型，点击确定即可

#### 更改“桌面”文件夹位置

#### 更改“回收站”文件夹位置

#### Temp文件

- 介绍：Temp文件夹用来存储在文件操作过程中的临时文件，比如安装软件、解压缩等等

- 可能位置：C:\Users\YourUserName\AppData\Local\Temp

  可以通过按下Win+R，输入%temp%快速打开Temp文件夹

- 可能的危险：基本无
- 清理方法：
  - 方法一：使用Windows“磁盘清理”工具或大部分杀毒软件自带的垃圾清理功能即可
  - 方法二：手动删除Temp文件夹下的所有文件，对于占用的文件，直接跳过即可

#### 聊天记录文件

- 以下软件的聊天记录文件默认存储在C盘，可在软件设置中更改存储位置
  - QQ
  - 微信
  - 钉钉

### 2. 常用软件

#### pip

- 介绍：pip在安装安装Python库时，如果之前已经下载过该库，pip会默认使用缓存来安装库，而不是重新从网络上下载。缓存文件通常存储在用户目录下的缓存文件夹中，查找的命令为：

  ````bash
  pip cache dir
  ````

- 可能位置：C:\Users\YourUserName\Appdata\Local\pip\cache

​	（注：不同虚拟环境都是共享这些cache的）

- 可能的危险：无

- 清理方法：

  使用

  ```bash
  pip cache list
  ```

  查看所有缓存的库；

  使用

  ```bash
  pip cache remove package-name
  ```

  来清理特定库；

  使用

  ```bash
  pip cache purge
  ```

  清理所有缓存的库。

#### miniconda

- 介绍：miniconda会默认把新的虚拟环境创建在C盘下，我们可以将其迁移到其他地方

- 可能的位置：C:\Users\YourUserName\\.condarc

- 可能的危险：无

- 清理方法：

  1. 打开C:\Users\YourUserName\\.condarc文件

  2. 修改

     ```yaml
     env_dirs:
       - 这里是你想要虚拟环境的路径，比如D:\conda_envs
     pkgs_dirs:
       - 这里是你想要的package暂存路径，比如D:\conda_pkgs
     ```
  3. 在命令行中输入

     ```bash
     conda info
     ```
     可以确认是否修改成功

  4. **注意!** 输入conda info后，请保证base environment的路径后有(writable)字样，表示该路径是可写的
#### Pr

- 介绍：Pr会默认缓存视频图像文件到C盘

- 可能位置：C:\Users\YourUserName\Appdata\Roaming\Adobe\Common

- 可能的危险：无

- 清理方法：

  1. 打开Premiere Pro，选择**编辑** > **首选项** (Windows) > **媒体缓存**或 **Premiere Pro** > **设置** (macOS) > **媒体缓存**

  2. 要移除媒体缓存文件，请单击**移除媒体缓存文件**旁边的**删除**按钮

     ![](https://helpx-prod.scene7.com/is/image/HelpxProdLoc/clear_cache-9?$pjpeg$&jpegSize=300&wid=1600)

     参考：[清理Pr缓存](https://helpx.adobe.com/cn/premiere-pro/kb/clear-cache.html)

#### Unity

- 介绍：Unity从package manager导入各种插件时，会进行缓存以加速下次打开项目

- 可能位置：C:\users\YourUserName\Appdata\Local\Unity\cache

- 可能的危险：使下一次打开项目时间变长

- 清理方法：删除cache的子文件夹npm和packages的内容

  参考：[如何清理Unity占用的C盘空间](https://developer.unity.cn/projects/60f38b25edbc2a43884e6920)

#### Mathematica

- 介绍：Mathematica附带的离线文档

- 可能位置：C:\Users\YourUserName\AppData\Local\Programs\Common\Wolfram␣Research\Documentation.en-us\YourVersion\Documentation\English

  或

  C:\Users\YourUserName\AppData\Local\Programs\Common\Wolfram␣Research\Documentation.zh-Hans-cn\YourVersion\Documentation\SimplifiedChinese

- 可能危险：无

- 清理：（请先保证Mathematica的安装路径不在C盘）

  1. 打开Mathematica，输入`$InstallationDirectory`，查看输出的安装目录，例如：D:\Program␣Files\Wolfram␣Research\Mathematica\YourVersion

  2. 创建或进入已有文件夹$InstallationDirectory\Documentation，直接将原先的English或SimplifiedChinese文件夹移动过来即可。例如，原先的文档路径

     > C:\Users\YourUserName\AppData\Local\Programs\Common\Wolfram␣Research\Documentation.zh-Hans-cn\YourVersion\Documentation\SimplifiedChinese

     新的文档路径应为

     > D:\Program␣Files\Wolfram␣Research\Mathematica\YourVersion\Documentation\SimplifiedChinese

     即直接移动SimplifiedChinese文件夹，其中"D:\Program␣Files\Wolfram␣Research\Mathematica\YourVersion"为`$InstallationDirectory`的输出值

  3. 重启Mathematica，按下F1，若成功启动离线文档，无"paclet:guide/WolframRoot" could not be found."报错，即为成功

#### Autodesk

### 3. 常见游戏、启动器等

