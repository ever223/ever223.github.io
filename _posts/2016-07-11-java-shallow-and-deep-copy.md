---
layout: post
title: "Java中的浅拷贝与深拷贝"         # title of the post
description: "介绍Java中的浅拷贝与深拷贝"
date:   2016-07-11 13:56:31
modified: 2016-07-16 22:56:31       
category: java
tags: ['Java']
excerpt: "Java中的浅拷贝与深拷贝定义、实现"
comments: true
---


## 1.定义
**浅拷贝(shallow copy):** 使用一个已知实例对新创建实例的成员变量逐个赋值，即拷贝对象时仅仅拷贝对象本身（包括对象中的基本变量），而不拷贝对象包含的引用指向的对象。
**深拷贝(deep copy):** 当一个类的拷贝构造方法，不仅要复制对象的所有非引用成员变量值(基本数据类型)，还要为引用类型的成员变量创建新的实例，并且初始化为形式参数实例值。
如果一个对象的成员变量都是基本数据类型的时候，则此时浅拷贝相当于深拷贝；而如果其中一个成员变量为引用对象时：只将该成员变量的引用赋值给新拷贝的对象，则为浅拷贝；若将该成员变量新生成一个实例赋值给新拷贝的对象，则为深拷贝。

## 2.Java拷贝操作类型
java中的拷贝类型有三种：operator=、拷贝构造函数和clone()方法。但是java不支持运算符重载，所以在自定义类型中无法定义operator=。

| 类型 | operator= | 拷贝构造函数 | clone() |
|:-------------|:-------------|:-----|:-----|
|预定义基本类型|深拷贝|如果支持拷贝构造函数的类型，则是深拷贝|不支持|
|自定义对象|浅拷贝|取决于实现|取决于实现|
|预定义结合类型|浅拷贝|会逐个调用每个元素的operator=方法|会逐个调用每个元素的operator=方法|


- 首先测试的是预定义非集合类型的operator =操作

```java
/**
 * @AUTHOR: xiaoo_gan
 * @DATE: 2016-07-09 14:33.
 * @DESCRIPTION:
 */
public class OperatorTest {
     public static void main(String[] args) {
         int x = 1;
         int y = x;
         x = 2;
         System.out.println("基本类型是否为浅拷贝:" + (x == y));
     }
}
```
- 拷贝构造函数

```java
	/**
	 * @AUTHOR: xiaoo_gan
	 * @DATE: 2016-07-09 14:59.
	 * @DESCRIPTION:
	 */
	public class Address {
	    private String detail;
	    private String zipCode;
	
	    public Address(String detail, String zipCode) {
	        this.detail = detail;
	        this.zipCode = zipCode;
	    }
	    // 拷贝构造函数
	    Address(Address address) {
	        this.detail = address.detail;
	        this.zipCode = address.zipCode;
	    }
	}


/**
 * @AUTHOR: xiaoo_gan
 * @DATE: 2016-07-09 14:59.
 * @DESCRIPTION:
 */

public class User {
    private String name;
    private int age;
    private Address address;

    public User(String name, int age, Address address) {
        this.name = name;
        this.age = age;
        this.address = address;
    }

    // 拷贝构造函数
    User(User user) {
        this.name = user.name;
        this.age = user.age;
        this.address = user.address; //直接将address赋值给新拷贝的User，为浅拷贝；新拷贝的User与原User共享同一个Address；
        //this.address = new Address(user.address); //通过原User的地址新创建一个地址实例赋值给新拷贝的User，为深拷贝；
    }

    public static void main(String args[]) {
        Address address1 = new Address("地址1", "422811");
        User user1 = new User("用户1", 24, address1);
        User user2 = new User(user1);
    }
}
```

- clone()方法
虽然Clone方法在Object中存在的，但是如果想要调用clone必须实现Cloneable接口，否则会抛出java.lang.CloneNotSupportedException。

```java
/**
 * @AUTHOR: xiaoo_gan
 * @DATE: 2016-07-09 15:26.
 * @DESCRIPTION:
 */
public class AddressCloneable  implements Cloneable {
    private String detail;
    private String zipCode;

    public AddressCloneable(String detail, String zipCode) {
        this.detail = detail;
        this.zipCode = zipCode;
    }

    protected Object clone() throws CloneNotSupportedException {
        // Address中都为不可变类型，故为深拷贝
        return super.clone();
    }
}

/**
 * @AUTHOR: xiaoo_gan
 * @DATE: 2016-07-09 15:28.
 * @DESCRIPTION:
 */
public class UserCloneable implements Cloneable {
    private String name;
    private int age;
    private AddressCloneable address;

    public UserCloneable(String name, int age, AddressCloneable address) {
        this.name = name;
        this.age = age;
        this.address = address;
    }

	//浅拷贝
    protected Object clone() throws CloneNotSupportedException {
        // UserCloneable中存在引用对象，浅拷贝
        return super.clone();
    }
}
```

若将UserCloneable的clone方法改为

```java
    // 深拷贝
    protected Object clone() throws CloneNotSupportedException {
        UserCloneable userCloneable = (UserCloneable) super.clone();
        // 对AddressCloneable也进行了深拷贝
        userCloneable.address = (AddressCloneable) userCloneable.address.clone();
        return userCloneable;
    }
```
