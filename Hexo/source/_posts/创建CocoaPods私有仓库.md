---
title: 创建CocoaPods私有仓库
date: 2019-04-04 15:15:36
tags: 
- iOS
categories: 
- 文档
---

# 创建CocoaPods私有仓库

1. 创建版本库（*用于存放版本*）

   * 从Git服务器创建一个私有仓库

   ![创建版本库](https://i.loli.net/2019/04/03/5ca44bfeee983.png)

   * 打开终端输入代码

     ```shell
     $ pod repo add GJRepo https://github.com/gjhealth/GJRepo.git
     ```

   * 查看目录 `~/.cocoapods/repos` 显示如下图，除master之外会增加一个版本仓库

     ![repos目录](https://i.loli.net/2019/04/03/5ca44f78bf4da.png)

2. 创建私有代码仓库（*用于存放自定义控件*）

   * 创建仓库同时勾选 `MIT License` 和 `README`

     ![自定义组件库](https://i.loli.net/2019/04/03/5ca452760e36a.png)

   * 克隆项目到本地并添加文件`代码`、`仓库名.podspec`、`.swift-version`

     ![文件目录](https://i.loli.net/2019/04/03/5ca453862b555.png)

     > `.swift-version`文件用来指导swift版本

     ```shell
     $ echo "3.0" > .swift-version
     ```

     > `.podspec`代码库pod描述文件，可以通过指令创建空白模板

     ```shell
     $ pod spec create MyLib
     ```

     或者拷贝下面模板进行修改

     ```json
     Pod::Spec.new do |s|
       s.name         = "MyAdditions" # 项目名称
       s.version      = "0.0.1"        # 版本号 与 你仓库的 标签号 对应
       s.license      = "MIT"          # 开源证书
       s.summary      = "私人pod代码" # 项目简介
     
       s.homepage     = "https://git.oschina.net/baiyingqiu/MyAdditions" # 仓库的主页
       s.source       = { :git => "https://git.oschina.net/baiyingqiu/MyAdditions.git", :tag => "#{s.version}" }#你的仓库地址，不能用SSH地址
       s.source_files = "MyAdditions/*.{h,m}" # 你代码的位置， BYPhoneNumTF/*.{h,m} 表示 BYPhoneNumTF 文件夹下所有的.h和.m文件
       s.requires_arc = true # 是否启用ARC
       s.platform     = :ios, "7.0" #平台及支持的最低版本
       # s.frameworks   = "UIKit", "Foundation" #支持的框架
       # s.dependency   = "AFNetworking" # 依赖库
     
       # User
       s.author             = { "BY" => "qiubaiyingios@163.com" } # 作者信息
       s.social_media_url   = "http://qiubaiying.github.io" # 个人主页
     
     end
     ```

     > 验证仓库是否正确

     ```shell
     $ pod lib lint
     ```

     > 验证并没问题后添加`--allow-warnings`就可以通过验证了

     ```shell
     $ pod lib lint --allow-warnings
     ```

     > 验证后显示

     ```shell
      -> MyAdditions (0.0.1)
     
      MyAdditions passed validation.
     ```

3. 将描述文件推送到版本库

   - 将项目打标签并推送到远程仓库，标签号和版本号对应。然后将代码仓库描述信息push到版本仓库

     ```
     $ pod repo push MyRepo GJLib.podspec --allow-warnings
     ```

     当验证成功后`~/.cocoapods/repos/MyRep`目录下回新增仓库的描述信息

     ![repos目录](https://i.loli.net/2019/04/03/5ca4673f2cd1a.png)

4. 私有pod库的使用

   - 编辑`Podfile`添加私有版本库和公有库地址，如下

     ```
     source ‘https://github.com/CocoaPods/Specs.git’
     source ‘https://git.oschina.net/baiyingqiu/MyRepo.git’
     
     platform :ios, '8.0'
     
     target ‘MyPodTest’ do
     use_frameworks!
     
     pod “BYPhoneNumTF” #公有库
     pod ‘GJLib’ #我们的私有库
     pod ‘GJTest’ #这是我又添加到版本库中的另一个代码库
     
     end
     ```

   - 执行`pod install`

> **参考文章**：
> 
> [https://www.jianshu.com/p/0c640821b36f](https://www.jianshu.com/p/0c640821b36f)
> 
> [https://blog.csdn.net/qq_19957803/article/details/78656688](https://blog.csdn.net/qq_19957803/article/details/78656688)
