---
layout: post

title:  CocoaPods简单使用

date:   2016-09-19 16:10:00 +0800

categories: document

tag: demo
---

* content
{:toc}


首先创建__Podfile__,在终端进入你项目所在的目录（__cd__ + 拖拽项目到终端里面获取路径），
`boon:~ aaaa$cd /XXX //当前项目路径`

然后在该目录下利用__vi__ 创建__Podfile__，运行：
`boon:~ aaaa$vi Podfile`
然后在Podfile文件中输入以下信息（关于vi基本使用后文总结）：
    `platform :iOS, '8.0'`
    `pod 'ReactiveCocoa','2.1.8'`//_指定版本号_的可以获取特定版本，_不指定版本号_的将获取最新的版本。
  然后保存退出，vim环境下，先按__ESC__退出编辑状态,然后输入保存退出命令：
  `:wq`
退出后使用`ls -la`命令查看目录下文件，多了一个名字为Podfile的文件，文件内容为刚刚输入的内容。tips：Podfile文件应该和工程文件.xcodeproj在同一个目录下。
现在，可以利用CocoPods下载ReactiveCocoa等类库了。
在终端中的当前项目目录下运行命令：
`$pod install` //初始安装

`$pod update` //用于更新

Updating local specs repositories问题解决方法如下：
`pod install` 换成`pod install --verbose --no-repo-update`这个命令，前面的命令被墙了，感觉变快了。

在导入库文件不确定全名或者版本号时可以进行搜索，cocopods提供搜索功能，命令如下：
`boon:~ aaaa$pod search XXX`  //XXX为需要搜索的库名称

***
补充一下CocoaPods的安装过程：
      需要用到Ruby环境，Mac系统自带ruby，但是ruby的软件源ruby gems.org被墙了，如果没翻出去的话，最好先更换一下源，
1、删除默认源，`$gem sources --remove https://rubygems.org/`
2、添加淘宝的源，`$gem sources -a https://ruby.taobao.org/`
3、查看，`$gem sources -l`

升级一下gem
`$sudo gem update --system`

完了就开始安装CocoaPods了
`$sudo gem install cocoapods`
`$pod setup`

***
>补充一下出现Setting up CocoaPods master repo 没有任何反应的问题，一般的原因是cocoa pods.org被墙了
gitcafe和oscchina都是国内的服务器，可以使用它们的CocoaPods索引库的镜像：
