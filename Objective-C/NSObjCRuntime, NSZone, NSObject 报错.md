### NSObjCRuntime, NSZone, NSObject 报错

项目链接OC与C混编的问题，编译的时候遇到了问题。遇到了NSObjCRuntime, NSZone, NSObject报错的问题

由于 prefix 文件没有区分是否是 oc 文件，对 C 文件也import了 OC 的framework。

解决方案就是 在 prefix 文件之中 的 oc framework 添加

```objc
#ifdef __OBJC__

#endif
```

同时，在引用C++的文件```.m ```改成 ```.mm```