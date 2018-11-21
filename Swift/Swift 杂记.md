## Swift 杂记

#### 1. 动态计算状态栏，导航栏高度

```swift
let statusRect = UIApplication.shared.statusBarFrame 
let navigaRect = self.navigationController?.navigationBar.frame
```