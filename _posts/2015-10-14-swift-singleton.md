---
layout: post
title: swift单例模式
date: 2015-10-13 11:29
modified: 				
category: iOS
tags: ["iOS", "swift"]
excerpt: 介绍swift中的三种单例模式的方法。
comments: true
---

# 方法一： Class constant
静态常量

```swift
class SingletonA {

    static let sharedInstance = SingletonA()

    init() {
        println("AAA");
    }

}
```

# 方法二：Nested struct
在方法内定义静态常量

```swift
class SingletonB {

    class var sharedInstance: SingletonB {
        struct Static {
            static let instance: SingletonB = SingletonB()
        }
        return Static.instance
    }

}
```

#方法三：dispatch_once
使用dispatch_once可以保证其中的代码只执行一次

```swift
class SingletonC {

    class var sharedInstance: SingletonC {
        struct Static {
            static var onceToken: dispatch_once_t = 0
            static var instance: SingletonC? = nil
        }
        dispatch_once(&Static.onceToken) {
            Static.instance = SingletonC()
        }
        return Static.instance!
    }
}
```

[原文地址](https://github.com/hpique/SwiftSingleton)

