# TTLaunchKit

[![CI Status](https://img.shields.io/travis/claudeli@yeah.net/TTLaunchKit.svg?style=flat)](https://travis-ci.org/claudeli@yeah.net/TTLaunchKit)
[![Version](https://img.shields.io/cocoapods/v/TTLaunchKit.svg?style=flat)](https://cocoapods.org/pods/TTLaunchKit)
[![License](https://img.shields.io/cocoapods/l/TTLaunchKit.svg?style=flat)](https://cocoapods.org/pods/TTLaunchKit)
[![Platform](https://img.shields.io/cocoapods/p/TTLaunchKit.svg?style=flat)](https://cocoapods.org/pods/TTLaunchKit)

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements
    1.广告页加载思路。广告页的内容要实时显示，在无网络状态或者网速缓慢的情况下不能延迟加载，或者等到首页出现了再加载广告页。所以这里我不采用网络请求广告接口获取图片地址，然后加载图片的方式，而是先将图片异步下载到本地，并保存图片名，每次打开app时先根据本地存储的图片名查找沙盒中是否存在该图片，如果存在，则显示广告页。

    2.判断广告页面是否更新。无论本地是否存在广告图片，每次启动都需要重新调用广告接口，根据图片名称或者图片id等方法判断广告是否更新，如果获取的图片名称或者图片id跟本地存储的不一致，则需要重新下载新图片，并删除旧图片。

    3.广告页点击。如果点击广告需要跳转广告详情页面，那么广告链接地址也需要用NSUserDefaults存储。注意：广告详情页面是从首页push进去的。

    4.广告页的显示代码可以放在AppDeleate中，也可以放在首页的控制器中。如果代码是在AppDelegate中，可以通过发送通知的方式，让首页push到广告详情页。

    5.广告页面的底部和启动图的底部一般都是相同的，给我们的感觉就是启动图加载完之后把广告图放在了启动图上，而且不能有偏差，比如淘宝。美工在制作广告图的时候要注意这点。

    6.研究了一下淘宝的广告显示机制，删除淘宝之后重新打开或者每天第一次打开不会显示广告图片，第二次打开才会显示。美团的广告图有时候一直都不会显示，所以后台在开发广告api的时候可以增加个字段来判断是否启用广告，如果后台关闭了广告，将沙盒中的图片删除即可。
    
    use:
    see Example
## Installation

TTLaunchKit is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'TTLaunchKit'
```

## Author

claudeli@yeah.net

## License

TTLaunchKit is available under the MIT license. See the LICENSE file for more info.
