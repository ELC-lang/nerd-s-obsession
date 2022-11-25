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
