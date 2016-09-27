---
published: true
title: Xcode build tools
layout: post
---
Title: 

title: Xcode build tools  
date: 2016-06-02  
tags:

-   Xcode
-   iOS  
    ---



Xcode 固定每年會更新一次以上，更新後的 Xcode 最麻煩的一件事情原本在舊版本可以正常無誤 build ，更新後卻無法正常 build，小一點的只要小修改，嚴重的話幾乎要花上一整天的時間再修改設定，使用 pod 可以把問題降到最少。

# Pod

Pod 用來管理第三方支援庫，也可以用來管理自己的支援庫，強烈推薦使用。在 wTHSR 專案中也使用了 pod。

## 安裝

```shell
sudo gem install pod
```

## 使用

```shell
pod init
```

編輯 Podfile

```shell
pod install
```


# fastlane

這套工具包含了 scan(測試)，gym(build)，snapshot(螢幕擷取)，deliver(上傳)

## 安裝

```shell
sudo gem install fastlane
```

## 使用

在專案目錄下執行以下指令

```shell
fastlane init
```

````````
Your Apple ID (e.g. fastlane@krausefx.com): (輸入 iTunes connect Apple ID)
Password (for xxxxxx): (輸入密碼)
App Identifier (com.krausefx.app): (輸入 app ID, 格式是倒過來的 domain ， com.yourcompany.name)
Would you like to create your app on iTunes Connect and the Developer Portal? (y/n)
Optional: The scheme name of your app (If you don't need one, just hit Enter):
````````

最後會產生一個 fastlane 目錄

## gym(build)

```shell
gym init

Select Scheme:

1.  wTHSR
2.  Pods-wTHSR
3.  SBJson
4.  VTAcknowledgementsViewController
```

第一次使用 `init` 產生設定檔案


```shell
gym
```

在終端機下編譯專案，後會產生一個 .ipa 用來上傳到 iTunes Connect


## snapshot(螢幕擷取)

1. 使用 `init` 產生設定檔案

```shell
snapshot init
```

2. 開啟 Xcode 在 UITest 專案錄製要擷取的畫面

3. `snapshot` 自動擷取畫面，模擬器不要縮放，縮小後會擷取到縮小的尺寸。

```shell
snapshot
```


## deliver(上傳)

1. 使用 `init` 產生設定檔案

```shell
deliver init
```

會自動連結到網站產生所有的資料

2. 編輯或修改設定檔案

3. 上傳

```shell
deliver --ipa "./build/wTHSR.ipa"`
```
