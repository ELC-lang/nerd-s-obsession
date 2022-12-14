# an title

来让我们看看这里有些什么！  
这里存放的是elc的库所达到的成就，包括和stl一起跑benchmark或者对rand进行testu01的测试  
在这里你可以轻松的找到“某个elc的东西在某个测试中的表现如何”以及相关的代码链接  

我想以后这里的东西会越来越多  

## rand

elc的rand定义在`elc/base_defs`，点击[这里](https://github.com/ELC-lang/ELC/blob/master/parts/header_file/files/elc/_files/base_defs/base_defs/rand.hpp)查看具体的实现  
与`std::rand`和`std::mt19937`相比，elc的rand有更多的优点:

- [速度更快](https://steve02081504.github.io/gbenchmark_webui/?file=https%3A%2F%2Fraw.githubusercontent.com%2FELC-lang%2FELC%2Fmaster%2Fparts%2Fheader_file%2Ftest%2Felc_rand_VS_std_BENCHMARK%2Fresult.json)
- 更好的随机性（通过了`std`中的`rand`和`mt19937`未能通过的[testu01测试](https://github.com/ELC-lang/ELC/blob/master/parts/header_file/test/elc-rand-testU01/output.txt)）
- 更好的可移植性（在不同的平台上都能保证同一种子下随机出一致的结果，而`std::rand`不行）
- 泛型支持（可以用于任何平凡构造的类型）
- 比`std::rand`更长的周期以及比`std::mt19937`更小的状态，一切都刚刚好够用  

[在在线编译中使用elc::rand的示例](https://godbolt.org/z/cY9Ka8vhf)  

## string

elc的string定义在`elc/string`，点击[这里](https://github.com/ELC-lang/ELC/tree/master/parts/header_file/files/elc/_files/string)查看具体的实现  
与`std::string`相比，elc的string有更多的优点:

- copy-on-write  
- 更小的空间占用  
- 更快的头插速度  
- 更多的接口（包括但不限于查看当前内存占用、预先分配一段内存、`pop_fount`等等）  
- 更好的编译期常量支持  
- 近乎常数时间的`substr`、`hash`、`operator==`、定长构造等  
- 其他elc函数的支持（比如不同于`std::to_string`的可以进行无损来回转换的`elc::to_string`等）

与`std::string`一同benchmark的结果[点此查看](https://steve02081504.github.io/gbenchmark_webui/?file=https%3A%2F%2Fraw.githubusercontent.com%2FELC-lang%2FELC%2Fmaster%2Fparts%2Fheader_file%2Ftest%2Felc_string_VS_std_string_BENCHMARK%2Fresult.json)  
[在在线编译中使用elc::string的示例](https://godbolt.org/z/3eav315a1)  

需要注意的是，在上面的在线编译示例中目前有两个小问题，一个是编译器的ice（会导致程序崩溃），而另一个是STL的实现问题（导致编译中警告）  
编译器ice绝赞调查中，[详见此处](https://developercommunity.visualstudio.com/t/Optimisation-makes-code-crash/10215710)  
STL的实现问题已经在<https://github.com/microsoft/STL/issues/3246>被修复，等待下一版本的更新即可  

## io

elc的io定义在`elc/stream`，由于实现较为分散，所以这里只给出`base_stream`的实现链接，[点此查看](https://github.com/ELC-lang/ELC/tree/master/parts/header_file/files/elc/_files/base_stream)  
与`std`中的io相比，elc的io有更多的优点：

- 指针输出包含更详细的信息（包括指针指向的类型名称和指针的值）  
- 作为utf32的`elc::char_t`原生支持  
- 得益于`elc::to_string`，无损并且高精度的算数类型转换  
- 更为完善的输出逻辑（比如对于非`true`也非`false`的`bool`值，相比`std`的大部分实现而言，elc的输出会是`other(值内容)`，而不是`true`）

[在在线编译中使用elc::out的示例](https://godbolt.org/z/55KGGPrGY)  
