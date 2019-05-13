# SingletonTemplate
Objective-C 创建安全的单例类

例如我需要创建一个名为“GlobarManager”的单例类

.h头文件：
```
#define  GLOBARMANAGER [[GlobarManager alloc] init]
@interface GlobarManager : NSObject
AL_AS_SINGLETON; //在头文件中加入这个宏
@property (nonatomic, strong) NSString *name;
@end
```
.m实现：
```
@implementation GlobarManager
AL_SYNTHESIZE_SINGLETON(GlobarManager); //.m文件中加入这个宏

// 需要注意的是， 初始化不能直接用 init 方法， 需要用 singletonInit
- (void)singletonInit {
    // 初始化代码写这里
    _name = @"Tom";
}

// your code here ...

@end
```

需要调用这个单例类时
可使用宏定义
```
GLOBARMANAGER.name = @"Bob";
NSLog(@"%@", GLOBARMANAGER.name);
```
或直接初始化
```
GlobarManager *global = [[GlobarManager alloc] init];
global.name= @"Bob";
```
