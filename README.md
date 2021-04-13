# Rime 鼠须管输入法傻瓜式配置指南
  OS:Windows 10 20H2
  
  version: 0.0.1
  
  Date:2021-04-13
  
  ----
  # 是这个https://github.com/wongdean/rime-settings 在windows上的设置方法，所以就没怎么更改
  本仓库为 Rime 鼠须管输入法的配置文件，特点有：
  1. 简单易用，不需要代码基础。皮肤与macOS自带输入法皮肤比较相似
  2. 支持 emoji 候选，支持符号快捷输入，支持中英文混合输入，支持`/`+关键词实现快捷输入
  3. 配置了部分网络上的词库，单词库来讲，已经非常强大，全新配置的话，最多一周就非常顺手
  4. 配置文件支持 Rime 鼠须管0.14.0(macOS)、Weasel 小狼毫0.14.3(Windows)，Linux,功能上都没有问题。


  ## 注意！！！
  如使用本方案，请全部下载覆盖然后重新加载（记得备份您原来的配置）
  除非您对配置文件很熟悉，否则可能会出现各种问题，恕我无法一一排查

  
  ## 用法
  1. 安装Rime输入法windows 小狼毫,并注销或重启
  2. 下载仓库所有配置文件到本地
  3. 安装字体文件(font 文件夹内的两个文件)
  4. 右下角打开小狼毫用户设定，会弹出用户设定文件夹  
  5. 将下载的除字体外的所有文件覆盖到用户设定文件夹  
  6. 右上角菜单栏点击小狼毫图标，点击重新部署，部署完毕即可用
  
  
  ## 配置文件说明
  - `default.custom.yaml` 设置输入法、如何切换输入法、翻页等
  - `squirrel.custom.yaml` 设置哪些软件默认英文输入，输入法皮肤等
  - `custom_phrase.txt` 设置快捷输入，修改完成后要重新部署才能生效
  配置文件中大部分都有注释。

  ## 几个你可能会关注的问题
  ### 1、怎么添加输入法皮肤？
  该配置默认只有3种皮肤，添加皮肤的方法如下：
  先添加皮肤配置到`squirrel.custom.yaml` 文件，
  再将`squirrel.custom.yaml`中的输入法配置，复制添加到`weasel.custom.yaml`之中，在输入法设定中即可看到新增加的皮肤。

  ### 2、编辑拓展词库？
  将词库文件拷贝到文件夹，修改 `luna_pinyin.extended.dict.yaml`文件

  将词库名字加在 `import_tables` 下(注意格式)
  
  可以用深蓝词库转换，转为Rime词库格式。转换后必须在开头添加
  ---
  name: luna_pinyin.shopping
  version: "2016.10.29"
  sort: by_weight
  use_preset_vocabulary: true
  ...

  重新部署即可

  **默认没有启用那么多的词库，如有需要请至上述文件中取消注释即可**
  
  ### 3、怎么添加自造词？
  添加至`custom_phrase.txt`文件中
  
  需要注意，输入的字母和汉字之间是 `tab`，而不是空格
  
  所以请使用不会自动替换`tab`为空格的编辑器修改此文件

  ### 4、emoji 的相关问题
  **emoji 显示方块**：下载除字体外的所有文件，然后重新部署，eomji 字符文件都在 `opencc` 文件夹中。

  **emoji 不显示**：<code>Ctrl + &#96;</code> (`Tab`上面那个)选“中/Y/半/汉"（可能是“中/N/半/汉"），第三项对应的是 emoji 的开关（可能指示的不准确），切换一下开关即可。


  **不需要 emoji**：同**emoji 不显示**，emoji 开关切换一下即可

  **已知 windows 显示的表情是黑白的，没有办法解决。**

  *如果彻底不需要表情，修改`default.custom.yaml`，`double_pinyin_flypy.custom.yaml`和`luna_pinyin.custom.yaml`（有注释）*
