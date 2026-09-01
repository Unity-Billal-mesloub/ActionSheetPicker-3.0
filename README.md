# ActionSheetPicker-3.0

[![Version](http://img.shields.io/cocoapods/v/ActionSheetPicker-3.0.svg)](http://cocoadocs.org/docsets/ActionSheetPicker-3.0)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Build Status](https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0/actions/workflows/CIBuild.yml/badge.svg)](https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0/actions/workflows/CIBuild.yml)
[![Issues](http://img.shields.io/github/issues/skywinder/ActionSheetPicker-3.0.svg)](https://github.com/skywinder/ActionSheetPicker-3.0/issues?state=open)
[![Platform](https://img.shields.io/cocoapods/p/ActionSheetPicker-3.0.svg)](http://cocoadocs.org/docsets/ActionSheetPicker-3.0)<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-24-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

## Important update

Now I fixed most of the things and merge PR' (thanks to [![All Contributors](https://img.shields.io/badge/all_contributors-20-orange.svg?style=flat-square)](#contributors-)).

I did much work to support this library from iOS 5. (and till iOS 26 and we keep going) 🚀

### [I still need help with the future support of this repo](https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0/issues). If you are interested  to help - please **drop a comment into  issue  🙏**

Regards, [Petr Korolev](https://github.com/Unity-Billal-mesloub)

---

- [Overview](#overview)
  - [Benefits](#benefits)
- [QuickStart](#quickstart)
  - [Basic Usage](#basic-usage)
- [Installation](#installation)
- [Example Projects](#example-projects)
- [Screenshots](#screenshots)
- [Apps using this library](#apps-using-this-library)
- [Maintainer and Contributor](#maintainer-and-contributor)
- [Contributing](#contributing)
- [Credits](#credits)
- [Contributors](#contributors)

Please welcome: **ActionSheetPicker-3.0**!

## ActionSheetPicker = UIPickerView + UIActionSheet

![Animation](Screenshots/example.gif)

Well, that's how it started. Now, the following is more accurate:

- _**iPhone/iPod** ActionSheetPicker = ActionSheetPicker = A Picker + UIActionSheet_
- _**iPad** ActionSheetPicker = A Picker + UIPopoverController_

## Overview

Easily present an ActionSheet with a PickerView, allowing the user to select from a number of immutable options.

### Benefits

- Spawn pickers with convenience function - delegate or reference
   not required. Just provide a target/action callback.
- Add buttons to UIToolbar for quick selection (see ActionSheetDatePicker below)
- Delegate protocol available for more control
- Universal (iPhone/iPod/iPad)

## QuickStart

There are 6 distinct picker view options:

- `ActionSheetStringPicker`
- `ActionSheetMultipleStringPicker`
- `ActionSheetDistancePicker`
- `ActionSheetDatePicker`
- `ActionSheetLocalePicker`
- `ActionSheetCustomPicker`

We'll focus here on how to use the `ActionSheetStringPicker` since it's most likely the one you want to use.

### Basic Usage

**For detailed info about customizations, please look  [BASIC USAGE](BASIC-USAGE.md)**

- Custom buttons view
- Custom buttons callbacks
- Action by clicking outside of the picker
- Background color and blur effect
- Other customizations

**For detailed examples, please check [Example Projects](#example-projects) in this repo.**

#### `Swift`

```swift
 ActionSheetMultipleStringPicker.show(withTitle: "Multiple String Picker", rows: [
            ["One", "Two", "A lot"],
            ["Many", "Many more", "Infinite"]
            ], initialSelection: [2, 2], doneBlock: {
                picker, indexes, values in

                print("values = \(values)")
                print("indexes = \(indexes)")
                print("picker = \(picker)")
                return
        }, cancel: { ActionMultipleStringCancelBlock in return }, origin: sender)
```

#### `Objective-C`

```obj-c
// Inside a IBAction method:

// Create an array of strings you want to show in the picker:
    NSArray *colors = @[@"Red", @"Green", @"Blue", @"Orange"];

// Done block:
    ActionStringDoneBlock done = ^(ActionSheetStringPicker *picker, NSInteger selectedIndex, id selectedValue) {
        NSLog(@"Picker: %@", picker);
        NSLog(@"Selected Index: %@", @(selectedIndex));
        NSLog(@"Selected Value: %@", selectedValue);
    };


// cancel block:
    ActionStringCancelBlock cancel = ^(ActionSheetStringPicker *picker) {
        NSLog(@"Block Picker Canceled");
    };

// Run!
    [ActionSheetStringPicker showPickerWithTitle:@"Select a Color" rows:colors initialSelection:0 doneBlock:done cancelBlock:cancel origin:sender];

```

## Installation

### CocoaPods

```ruby
pod 'ActionSheetPicker-3.0'
```

(**iOS 9 and later** compatible!)

[CocoaPods](http://cocoapods.org) is a dependency manager for Cocoa projects.

You can install it with the following command:

```bash
gem install cocoapods
```

To integrate ActionSheetPicker-3.0 into your Xcode project using CocoaPods, specify it in your `Podfile`:

Then, run the following command:

```bash
pod install
```

### Import to project

To import pod you should add string:

- For `Obj-c` projects:

```obj-c
   #import "CoreActionSheetPicker.h"
```

- For `Swift` projects:

```swift
  import CoreActionSheetPicker
```

### Carthage

Carthage is a decentralized dependency manager that automates the process of adding frameworks to your Cocoa application.

You can install Carthage with [Homebrew](http://brew.sh/) using the following command:

```bash
brew update
brew install carthage
```

To integrate ActionSheetPicker-3.0 into your Xcode project using Carthage, specify it in your `Cartfile`:

```ogdl
github "Unity-Billal-mesloub/ActionSheetPicker-3.0"
```

### Swift Package Manager

The [Swift Package Manager](https://swift.org/package-manager/) is a tool for automating the distribution of Swift code and is integrated into Xcode and the Swift compiler.

If you are using Xcode 11 or later:
 1. Click `File`
 2. `Swift Packages`
 3. `Add Package Dependency...`
 4. Specify the git URL for ActionSheetPicker-3.0.

```swift
https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0
```

### Manually

If you prefer not to use either of the aforementioned dependency managers, you can integrate ActionSheetPicker-3.0 into your project manually.

The "old school" way is manually added to your project all from [Pickers](CoreActionSheetPicker/CoreActionSheetPicker/Pickers) folder.

### Embedded Framework

- Add ActionSheetPicker-3.0 as a [submodule](http://git-scm.com/docs/git-submodule) by opening the Terminal, `cd`-ing into your top-level project directory, and entering the following command:

```bash
git submodule add https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0.git
```

- Open the `ActionSheetPicker-3.0` folder, and drag `CoreActionSheetPicker.xcodeproj` into the file navigator of your app project.
- In Xcode, navigate to the target configuration window by clicking on the blue project icon, and selecting the application target under the "Targets" heading in the sidebar.
- Ensure that the deployment target of CoreActionSheetPicker.framework matches that of the application target.
- In the tab bar at the top of that window, open the "Build Phases" panel.
- Expand the "Target Dependencies" group, and add `CoreActionSheetPicker.framework`.
- Click on the `+` button at the top left of the panel and select "New Copy Files Phase". Rename this new phase to "Copy Frameworks", set the "Destination" to "Frameworks", and add `CoreActionSheetPicker.framework`.

## Example Projects

`open ActionSheetPicker-3.0.xcworkspace`

Here is 4 projects:

- **CoreActionSheetPicker** - all picker files combined in one Framework.
- **ObjC-Example** - descriptive Obj-C project with many examples.
- **Swift-Example** - example, written on Swift. (only with basic Pickers examples, for all examples please run `ObjC-Example` project)
- **ACP-SPM-integration** - Swift Package Manager integration example.

## Screenshots

![ActionSheetPicker](Screenshots/string.png "ActionSheetPicker")
![ActionSheetDatePicker](Screenshots/date.png "ActionSheetDatePicker")
![ActionSheetDatePicker](Screenshots/time.png "ActionSheetDatePicker")
![CustomButtons](Screenshots/custom.png "CustomButtons")
![iPad Support](Screenshots/ipad.png "iPad Support")

## [Apps using this library](https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0/wiki/Apps-using-ActionSheetPicker-3.0)

If you've used this project in a live app, please let me know! Nothing makes me happier than seeing someone else take my work and go wild with it.

*If you are using `ActionSheetPicker-3.0` in your app or know of an app that uses it, please add it to [**this list**](https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0/wiki/Apps-using-ActionSheetPicker-3.0).*

## Maintainer and Contributor

- [Petr Korolev](http://github.com/Unity-Billal-mesloub) (update to iOS 7 and iOS 8, implementing new pickers, community support). I did much work to support this library from iOS 5. (and till iOS 26 and we keep going 🚀).

Now I fixed most of the things and merge PR' (thanks to [![All Contributors](https://img.shields.io/badge/all_contributors-20-orange.svg?style=flat-square)](#contributors-)!).

### [I still need help with the future support of this repo](https://github.com/Unity-Billal-mesloub/ActionSheetPicker-3.0/issues/348). If you are interested to help - please **drop a comment into  issue #348 🙏**

