---
layout: post
title: swift的一些知识，技巧
date: 2015-10-09 14:15
modified: 				
category: swift
tags: ["swift", "iOS"]
excerpt: swift的一些知识，技巧
comments: true
---

1. [安装cocoapods](#安装cocoapods)
1. [MARK、TODO、FIXME](#MARK、TODO、FIXME)
1. [.gitignore文件](#.gitignore文件)
1. [Controller的生命周期](#Controller的生命周期)

#安装cocoapods

```
先切换 gem 的源
$ gem sources --remove https://rubygems.org/

添加gem源
$ gem sources -a https://ruby.taobao.org/

查看源
$ gem sources -l
*** CURRENT SOURCES ***
https://ruby.taobao.org/

更新 gem
$ sudo gem update --system

$ vim .bash_profile
添加如下:
#GEM
GEM_HOME=$HOME/Software/ruby
export GEM_HOME
PATH=$PATH:$HOME/Software/ruby/bin
export PATH

$ source .bash_profile
$ gem install cocoapods
[...]
1 gem installed
$ pod --version
0.39.0
```


#MARK、TODO、FIXME
TODO: + 说明：
如果代码中有该标识，说明在标识处有功能代码待编写，待实现的功能在说明中会简略说明。
FIXME: + 说明：
如果代码中有该标识，说明标识处代码需要修正，甚至代码是错误的，不能工作，需要修复，如何修正会在说明中简略说明。

~~~swift
// MARK: your text goes here
// MARK: - your text goes here

// TODO: your text goes here
// FIXME: your text goes here
~~~

#.gitignore文件

~~~
# Xcode
.DS_Store
*/build/*
*.pbxuser
!default.pbxuser
*.mode1v3
!default.mode1v3
*.mode2v3
!default.mode2v3
*.perspectivev3
!default.perspectivev3
xcuserdata
profile
*.moved-aside
DerivedData
.idea/
*.hmap

#CocoaPods
Pods
~~~


#Controller的生命周期

```swift
import UIKit
//就是view的生命周期，下面已经按方法执行顺序进行了排序
class ViewController: UIViewController {

    //自定义控制器view，这个方法只有实现了才会执行
    override func loadView() {
        view = UIView()
    }
    // view是延迟加载，只要view加载完毕就调用这个方法
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    // view即将显示
    override func viewWillAppear(animated: Bool) {
        super.viewWillAppear(animated)
    }
    //view即将开始布局子控件
    override func viewWillLayoutSubviews() {
        super.viewWillLayoutSubviews()
    }
    // view已经完成子控件的布局
    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
    }
    // view已经出现
    override func viewDidAppear(animated: Bool) {
        super.viewDidAppear(animated)
    }
    // view即将消失
    override func viewWillDisappear(animated: Bool) {
        super.viewWillDisappear(animated)
    }
    // view已经消失
    override func viewDidDisappear(animated: Bool) {
        super.viewDidDisappear(animated)
    }
    // 收到内存警告
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
}
```
 
