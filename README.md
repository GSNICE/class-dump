# class-dump
基于class-dump源代码，解决报错的可用库。

# class-dump

class-dump，顾名思义，就是用来dump目标对象 的class信息的工具。它利用Objective-C语言的runtime 特性，将存储在Mach-O文件中的头文件信息提取出 来，并生成对应的.h文件。

## 下载

在github下载class-dump源码：

[nygard/class-dump: Generate Objective-C headers from Mach-O files. (github.com)](https://github.com/nygard/class-dump/)

**或直接下载本站class-dump源码。**

## 编译

使用Xcode打开项目工程：

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h67feopevuj219a0m2dk5.jpg)

选择class-dump后编译：

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h67feodxbuj21ao0u043e.jpg)

可能遇到报错：

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h67fenrlqgj21ao0u0agv.jpg)

注释后进行编译。

## 生成可执行文件

编译完成后会在以下目录中生成class-dump的可执行文件。

/Users/[用户名]/Library/Developer/Xcode/DerivedData/class-dump-cksscbidsnbpnubfttpknnwdogmk/Build/Products/Debug/class-dump

## 环境配置

将生成的可执行文件拷贝到以下目录下。

/usr/local/bin/

## 更改权限：终端输入

```Bash
sudo chmod 777 /usr/local/bin/class-dump
```

## 查看 class-dump 的一些基本参数

```Bash
class-dump --help
```

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h67femvkoej20ki0c9q4l.jpg)

到此class-dump安装和配置就完成了。

## 使用

```Bash
class-dump -H [app 路径] -o [输出头文件的路径]
// 示例：
// class-dump -H /Applications/Sketch\ 91.app -o /Users/[用户名]/Desktop/headercode
```

![](https://tva1.sinaimg.cn/large/e6c9d24ely1h67femmywej21980u0n57.jpg)

透过这些头文件，闭源App的程序架构就能初现端倪了，经验丰富的开发人员可以从中了解非常多的信息，这些信息是iOS逆向工程的基础。不过现在的 App 工程越来越大，而且还在不停地引用第三方代码，因此经常会发现 class-dump 出来了成百上千个头文件，虽然靠人工及经验一点点地分析是很好的练习方式，但过程实在太复杂，让人头大。需要通过各种工具逐步缩小目标范围，最后精准地定位目标函数。

值得注意的是，从AppStore下载的App都是经过加密的，可执行文件被加上了一层“壳”，class-dump应付不了这样的文件。所以还得需要其他工具把壳砸开才行。
