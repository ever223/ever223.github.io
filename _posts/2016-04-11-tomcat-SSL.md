---
layout: post
title: tomcat配置SSL
date: 2016-04-11 11:40
modified: 				
category: JAVA
tags: ["JAVA","tomcat"]
excerpt: tomcat配置SSL
comments: true
---

1. 生成证书
  
  ```
 $ JAVA_HOME/bin/keytool -v -genkey -alias tomcat -keyalg RSA -keystore /Users/xiaoo_gan/Downloads/tomcat.keystore
 $ JAVA_HOME/bin/keytool -exportcert -alias tomcat -keystore /Users/xiaoo_gan/Downloads/tomcat.keystore -file /Users/xiaoo_gan/Downloads/tomcat.cer
  ```
  按提示完成问答,即可生成证书  
  PS:问题 What is your first and last name? 填写本机IP地址，本地测试可以填写localhost
  
2. 配置`tomcat/conf/server.xml`
  
  找到如下注释
  
  ```xml
  <!-- Define a SSL HTTP/1.1 Connector on port 8443
         This connector uses the BIO implementation that requires the JSSE
         style configuration. When using the APR/native implementation, the
         OpenSSL style configuration is required as described in the APR/native
         documentation -->
    <!--
    <Connector port="8443" protocol="org.apache.coyote.http11.Http11Protocol"
               maxThreads="150" SSLEnabled="true" scheme="https" secure="true"
               clientAuth="false" sslProtocol="TLS" />
    -->
  ```
  
  改为
  
  ```xml
      <Connector port="8443" 
      protocol="HTTP/1.1" 
      SSLEnabled="true"   
      maxThreads="150" 
      scheme="https" 
      secure="true" 
      clientAuth="false" 
      keystoreFile="/Users/xiaoo_gan/Downloads/tomcat.keystore" 
      keystorePass="tomcat"
      sslProtocol="TLS" />
 ```
  `keystoreFile`: 为步骤1生成证书的位置  
  `keystorePass`: 为步骤1生成证书时设置的密码
  
3. 配置项目WEB_INF/web.xml (非spring－security项目)
  
  添加
  
  ```xml
      <login-config>
        <!-- Authorization setting for SSL -->
        <auth-method>CLIENT-CERT</auth-method>
        <realm-name>Client Cert Users-only Area</realm-name>
    </login-config>
    <security-constraint>
        <!-- Authorization setting for SSL -->
        <web-resource-collection>
            <web-resource-name>SSL</web-resource-name>
            <url-pattern>/*</url-pattern>
        </web-resource-collection>
        <user-data-constraint>
            <transport-guarantee>CONFIDENTIAL</transport-guarantee>
        </user-data-constraint>
    </security-constraint>
  ```
  