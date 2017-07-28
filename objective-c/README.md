# Objective-C


1.Objective-C 中的方法和属性，废弃(过期)的标注如下：

```Objective-C
@property (nonatomic, strong) UIColor *tintColor __attribute__((deprecated("review your color (it doesn't get darkened automatically anymore) and assign it 'backgroundTintColor' instead")));
@property (nonatomic, readwrite) NSUInteger selectedIndex __attribute__((deprecated("use 'setSelectedSegmentIndex:animated:' instead")));
- (void)setSelectedIndex:(NSUInteger)index animated:(BOOL)animated __attribute__((deprecated("use 'setSelectedSegmentIndex:animated:' instead")));
- (void)moveThumbToIndex:(NSUInteger)segmentIndex animate:(BOOL)animate __attribute__((deprecated("use 'setSelectedSegmentIndex:animated:' instead")));
```

2.NSObject 对象有一个 performSelector方法可以延时执行代码，没有必要创建定时器来处理。

``` Objective-C
[self performSelector:@selector(showUserInfoWithoutDelay) withObject:nil afterDelay:1.0f];
```