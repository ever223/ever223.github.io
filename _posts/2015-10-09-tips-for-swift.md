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

###1. MARK、TODO、FIXME
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

###2. .gitignore文件

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

###3. 
