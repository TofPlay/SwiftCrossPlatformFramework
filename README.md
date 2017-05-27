# Swift Cross Platform framework

---

## Table of contents

* [Introduction](#introduction)
* [Create an empty project](#create-an-empty-project)
* [Add targets](#add-targets)
  * [Target iOS](#target-ios)
  * [Target watchOS](#target-watchos)
  * [Target tvOS](#target-tvos)
  * [Target macOS](#target-macos)
* [Add "Sources" folder](#add-sources-folder)
* [Rename "info.plist"](#rename-infoplist)
  * [Info.plist for iOS](#infoplist-for-ios)
  * [Info.plist for watchOS](#infoplist-for-watchos)
  * [Info.plist for tvOS](#infoplist-for-tvos)
  * [Info.plist for macOS](#infoplist-for-macos)
* [Move all plist on "Sources" folder](#move-all-plist-on-sources-folder)
* [Update "Build Settings"](#update-build-settings)
  * [Set the product name](#set-the-product-name)
  * [Apply Product Name for all targets](#apply-product-name-for-all-targets)
* [Update packaging](#update-packaging)
  * [For iOS target](#for-ios-target)
  * [For watchOS target](#for-watchos-target)
  * [For tvOS target](#for-tvos-target)
  * [For macOS target](#for-macos-target)
* [One header file for all targets](#one-header-file-for-all-targets)
  * [Change header file](#change-header-file)
  * [Move header file to "Sources"](#move-header-file-to-sources)
  * [Update project](#update-project)
* [Add class for all platforms](#add-class-for-all-platforms)
* [Configure targets for Carthage](#configure-targets-for-carthage)
* [Configure project for SwiftPM](#configure-project-for-swiftpm)

---

## Introduction

The purpose of this tutorial is to create a Swift framework from the same sources for macOS, iOS, watchOS and tvOS platforms and use them in a project via Carthage. It will be also ready for SwiftPM.

## Create an empty project

1. Open Xcode 
2. Select `Create a new Xcode project`

![image](https://cloud.githubusercontent.com/assets/1082222/26510634/7a2033e4-425e-11e7-99cf-2644f8757ed3.png)

1. Select `Cross platform`
2. Click on `Empty`
3. Click on `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26510744/0addb1e0-425f-11e7-8725-282408c07a7c.png)

1. Enter the project name (for this tutorial we use `Template`)
2. Click on `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26511005/438fcbee-4260-11e7-9c06-db1b8eeef13f.png)

You should have this screen
![image](https://cloud.githubusercontent.com/assets/1082222/26509670/1604bd02-425a-11e7-915f-4e11affbfb2d.png)

## Add targets

We must add a target for each platform

### Target iOS

1. On the section **PROJECT** click on (+)

![image](https://cloud.githubusercontent.com/assets/1082222/26511084/ae34dae8-4260-11e7-83a3-aef1b6d8d1f1.png)

1. Select `iOS`
2. Select `Cocoa Touch Framework`
3. Click `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26511691/7a70d448-4263-11e7-8571-9e48716dcf3f.png)

1. Enter the project name `Template iOS` (replace `Template` by your framework name). Don't forget `iOS` it's important!
2. Click on `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26511331/db67b854-4261-11e7-8dd7-a0b718158f89.png)

You should have this screen
![image](https://cloud.githubusercontent.com/assets/1082222/26511421/42113968-4262-11e7-80c2-248e9d9e6431.png)

### Target watchOS

1. On the section **PROJECT** click on (+)

![image](https://cloud.githubusercontent.com/assets/1082222/26511514/b44fb5c2-4262-11e7-8f85-b95a5e5a48a5.png)

1. Select `watchOS`
2. Select `Watch Framework`
3. Click `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26511625/2e02a898-4263-11e7-9273-050494e662e1.png)

1. Enter the project name `Template watchOS` (replace `Template` by your framework name). Don't forget `watchOS` it's important!
2. Click on `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26511774/ca213212-4263-11e7-9c14-b5a0e2f390bf.png)

You should have this screen
![image](https://cloud.githubusercontent.com/assets/1082222/26511838/0a70e8ee-4264-11e7-9f39-ed9494308eb7.png)

### Target tvOS

1. On the section **PROJECT** click on (+)

![image](https://cloud.githubusercontent.com/assets/1082222/26511941/749b2fea-4264-11e7-9298-82116f8f8651.png)

1. Select `tvOS`
2. Select `TV Framework`
3. Click `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26512004/c8552924-4264-11e7-9d0e-44a0f5c9a7e8.png)

1. Enter the project name `Template watchOS` (replace `Template` by your framework name). Don't forget `watchOS` it's important!
2. Click on `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26512096/3fe8d332-4265-11e7-9c1f-25086bcf1a02.png)

You should have this screen
![image](https://cloud.githubusercontent.com/assets/1082222/26512123/6d574074-4265-11e7-870c-5fdf60242695.png)

### Target macOS

1. On the section **PROJECT** click on (+)

![image](https://cloud.githubusercontent.com/assets/1082222/26512220/e954aca2-4265-11e7-845b-120bad750435.png)

1. Select `macOS`
2. Select `Cocoa Framework`
3. Click `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26512316/49bf2e46-4266-11e7-8257-0a73cf5c0b4b.png)

1. Enter the project name `Template macOS` (replace `Template` by your framework name). Don't forget `macOS` it's important!
2. Click on `Next`

![image](https://cloud.githubusercontent.com/assets/1082222/26512402/ace38a94-4266-11e7-97d0-2530f1901286.png)

You should have this screen
![image](https://cloud.githubusercontent.com/assets/1082222/26512431/d4d37910-4266-11e7-99a9-102e3c9e7815.png)

## Add "Sources" folder 

1. Rigth click on `Template` and select `Add Files to Template`
2. Click on `New Folder`
3. Enter `Sources` and click on `Create` and `Add`

![image](https://cloud.githubusercontent.com/assets/1082222/26512914/09bafe44-4269-11e7-8d33-1d35d6082569.png)

## Rename "info.plist"

### Info.plist for iOS

1. Open folder `Template iOS`
2. Rename `info.plist` to `info-iOS.plist`

![image](https://cloud.githubusercontent.com/assets/1082222/26513141/388b4318-426a-11e7-9a21-f6c8ac201bdd.png)

### Info.plist for watchOS

1. Open folder `Template watchOS`
2. Rename `info.plist` to `info-watchOS.plist`

![image](https://cloud.githubusercontent.com/assets/1082222/26513200/7934017a-426a-11e7-940b-c5771b0779b2.png)

### Info.plist for tvOS

1. Open folder `Template tvOS`
2. Rename `info.plist` to `info-tvOS.plist`

![image](https://cloud.githubusercontent.com/assets/1082222/26513223/addc1886-426a-11e7-903a-032501b645a6.png)

### Info.plist for macOS

1. Open folder `Template macOS`
2. Rename `info.plist` to `info-macOS.plist`

![image](https://cloud.githubusercontent.com/assets/1082222/26513261/e0b8716e-426a-11e7-858c-5a3525c25c12.png)

## Move all plist on "Sources" folder

Select all on the folder

![image](https://cloud.githubusercontent.com/assets/1082222/26513344/44a9a206-426b-11e7-9977-d8de72f9cfd8.png)

And move them to the "Sources" folder

![image](https://cloud.githubusercontent.com/assets/1082222/26513403/977fb4a2-426b-11e7-9cb1-dd2e186d8657.png)

On the project remove plists

![image](https://cloud.githubusercontent.com/assets/1082222/26513496/0861cf34-426c-11e7-95fc-52548dc87441.png)

Rigth click on the `Sources` folder and click on `Add Files to "Template"...`

![image](https://cloud.githubusercontent.com/assets/1082222/26513514/2916d6ca-426c-11e7-8b61-3cfe70408d1a.png)

Select all plist and click on `Add`. Be careful don't check a target.

![image](https://cloud.githubusercontent.com/assets/1082222/26513580/8fb59be6-426c-11e7-88a7-6c8f74f42562.png)

## Update "Build Settings" 

### Set the product name

1. On section `PROJECT` select `Template`
2. Selection section `Build Settings`
3. In search enter `product name`
4. For the property `Product Name` enter `$(PROJECT_NAME)`

![image](https://cloud.githubusercontent.com/assets/1082222/26513843/17e25fb2-426e-11e7-8c46-5d88f9a3fadd.png)

### Apply Product Name for all targets

1. Select all targets
2. Click on `Product Name`
3. Click on key `Delete`. All targets will have the product name `Template`.

![image](https://cloud.githubusercontent.com/assets/1082222/26513965/ead10748-426e-11e7-8e43-cfda03ec19a1.png)

## Update packaging

### For iOS target

1. Select `Template iOS` target
2. Set property `info.plist File` to `Sources/info-iOS.plist`
3. Set property `Product Bundle Identifier` to `com.<your company>.$(PROJECT_NAME)`

![image](https://cloud.githubusercontent.com/assets/1082222/26514096/ee5b25aa-426f-11e7-8cb1-4e67b79d3e0c.png)

### For watchOS target

1. Select `Template watchOS` target
2. Set property `info.plist File` to `Sources/info-watchOS.plist`
3. Set property `Product Bundle Identifier` to `com.<your company>.$(PROJECT_NAME)`

![image](https://cloud.githubusercontent.com/assets/1082222/26514275/18daad9a-4271-11e7-9270-56f2e51b717a.png)

### For tvOS target

1. Select `Template tvOS` target
2. Set property `info.plist File` to `Sources/info-tvOS.plist`
3. Set property `Product Bundle Identifier` to `com.<your company>.$(PROJECT_NAME)`

![image](https://cloud.githubusercontent.com/assets/1082222/26514318/689e6268-4271-11e7-88b5-d2e1a44949fc.png)

### For macOS target

1. Select `Template tvOS` target
2. Set property `info.plist File` to `Sources/info-tvOS.plist`
3. Set property `Product Bundle Identifier` to `com.<your company>.$(PROJECT_NAME)`

![image](https://cloud.githubusercontent.com/assets/1082222/26514390/ba6a2aaa-4271-11e7-8ba9-7288bd599c38.png)

## One header file for all targets

### Change header file

1. Select `Template iOS.h`
2. Change `#import <UIKit/UIKit.h>` by `#import <Foundation/Foundation.h>`
3. Remove `iOS`

![image](https://cloud.githubusercontent.com/assets/1082222/26518766/481f6cee-42b7-11e7-95a7-f345742cae7e.png)

### Move header file to "Sources"

1. Open Finder and Rename `Template iOS.h` to `Template.h`
2. Move `Template.h` to folder `Sources`
3. Remove folders `Template iOS`, `Template macOS`, `Template tvOS` and `Template watchOS`

![image](https://cloud.githubusercontent.com/assets/1082222/26518853/f9f58f56-42b8-11e7-9e2e-99351d8e53d1.png)

![image](https://cloud.githubusercontent.com/assets/1082222/26518873/42349b5e-42b9-11e7-8233-e2c924cde0b5.png)

![image](https://cloud.githubusercontent.com/assets/1082222/26518883/6f19876a-42b9-11e7-8504-caa8bd24eb54.png)

### Update project

1. Remove folders `Template iOS`, `Template macOS`, `Template tvOS` and `Template watchOS`
2. Add `Template.h` in `Sources` folder
3. Select `Template.h`
4. In `Target Membership` check `Template iOS`, `Template watchOS`, `Template tvOS` and `Template macOS`
5. For each target select `Public` 

![image](https://cloud.githubusercontent.com/assets/1082222/26518921/07e49570-42ba-11e7-8432-ea8d49d61d31.png)

![image](https://cloud.githubusercontent.com/assets/1082222/26518944/4b812bea-42ba-11e7-9f9d-9866a9f20b2c.png)

![image](https://cloud.githubusercontent.com/assets/1082222/26519009/32d0ac82-42bb-11e7-8606-15ec4c18621f.png)

## Add class for all platforms

1. Click on `Sources`
2. Click on `New File...`

![image](https://cloud.githubusercontent.com/assets/1082222/26519048/d755fcd0-42bb-11e7-8361-d2c66ba75dfd.png)

1. Select `macOS`
2. Select `Swfit File`
3. Click `Next` button

![image](https://cloud.githubusercontent.com/assets/1082222/26519090/5fb6e530-42bc-11e7-991b-9f0eee7cf083.png)

1. Enter the name of your class
2. Select all targets 
3. Click `Create` button

![image](https://cloud.githubusercontent.com/assets/1082222/26519135/df5dec98-42bc-11e7-8651-0e1af611d5ec.png)

Your first class cross platform:
![image](https://cloud.githubusercontent.com/assets/1082222/26519150/417a6b68-42bd-11e7-99dc-cc7bae5d40b6.png)

## Configure targets for Carthage

1. Click on `Template iOS` option `Manage Schemes...`
2. For all targets check `Shared` 

![image](https://cloud.githubusercontent.com/assets/1082222/26519181/8f96de30-42bd-11e7-9a7c-54c5746f1b6b.png)

![image](https://cloud.githubusercontent.com/assets/1082222/26519206/e79f3a78-42bd-11e7-83fb-05adae300d5f.png)

## Configure project for SwiftPM

1. Select the project `Template`
2. Rigth click and select `New File...`

![image](https://cloud.githubusercontent.com/assets/1082222/26519283/eae645ea-42be-11e7-8c43-c70f0171ff0d.png)

1. Select `macOS`
2. Select `Swfit File`
3. Click `Next` button

![image](https://cloud.githubusercontent.com/assets/1082222/26519311/50d5eb08-42bf-11e7-83c7-a3cbfff38676.png)

1. Enter `Package`
2. Uncheck all targets
3. Click on `Create` button
4. On the `Package.swift` enter:

```swift
// swift-tools-version:3.1

import PackageDescription

let package = Package(
    name: "Template"
)
```

![image](https://cloud.githubusercontent.com/assets/1082222/26519345/eb672e3e-42bf-11e7-9acc-e04918478bb0.png)

![image](https://cloud.githubusercontent.com/assets/1082222/26519375/7e82e26c-42c0-11e7-9bc0-de752f80f556.png)
