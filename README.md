# SwiftUIPager

[![Swift Package Manager compatible](https://img.shields.io/badge/Swift%20Package%20Manager-compatible-brightgreen.svg)](https://github.com/apple/swift-package-manager)
[![CocoaPods platforms](https://img.shields.io/cocoapods/p/SwiftUIPager.svg)](https://cocoapods.org/pods/SwiftUIPager)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

SwiftUIPager provides  a `Pager` component built with SwiftUI native components. `Pager` is a horizontal view that will create a scrollable container to display a handful of pages. These pages are recycled on scroll, so you don't have to worry about memory issues. 

<img src="resources/example-of-usage.gif" alt="Example of usage"/>

## Requirements
* iOS 13.0+
* macOS 10.15+
* watchOS 6.0+
* Swift 5.1+

## Installation

### CocoaPods
```
pod 'SwiftUIPager'
```
### Swift Package Manager

Go to XCode:
* File -> Swift Packages -> Add Package Dependency...
* Use the URL https://github.com/fermoya/SwiftUIPager.git


## Usage

### Initialization

Creating a `Pager` is very simple. You just need to pass:
- `Binding` to page index
- Array of items that conform to `Equatable` and `Identifiable` 
- `ViewBuilder` factory method to create each page

```swift
 Pager(page: self.$pageIndex,
       data: self.items,
       content: { item in
           // create a page based on the data passed
           self.pageView(item)
 })
```

### UI customization

`Pager` is easily customizable through a number of view-modifier functions.  You can change the vertical insets, spacing between items or the page aspect ratio, among others:

```swift
Pager(...)
     .itemSpacing(10)
     .padding(8)
     .pageAspectRatio(0.6)
```
`pageAspectRatio` will change the look of the page. Use a value lower than 1 to make the page look like a card:

<img src="resources/page_aspect_ratio_lower_than_1.png" alt="PageAspectRatio lower than 1" height="640"/>

whereas a value greater than one will make it look like a box:

<img src="resources/page_aspect_ratio_greater_than_1.png" alt="PageAspectRatio greater than 1" height="640"/>

You can also use `interactive` to pass a shrink ratio that will be applied to those components that are not focused, that is, those elements whose index is different from `pageIndex` binding:

```swift
Pager(...)
    .interactive(0.8)
```

<img src="resources/interactive-pager.gif" alt="Interactive pager"/>

For more information, please check the [sample app](/Sample).

If you have any issues or feedback, please open an issue or reach out to me at [fmdr.ct@gmail.com](mailto:fmdr.ct@gmail.com).  
Please feel free to collaborate and make this framework better. 

### Events

Use `onPageChanged` to react to any change on the page index:

```swift
Pager(...)
     .onPageChanged({ (newIndex) in
         // do something
     })
```

## License  

`SwiftUIPager` is available under the MIT license. See the [LICENSE](/LICENSE) file for more info.
