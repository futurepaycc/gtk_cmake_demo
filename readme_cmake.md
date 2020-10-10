### 多目录可执行中
若目录名为hello, 千成不能! set(EXEC hello1), 这样会造成cp错误，原因不明

### 常用脚本
rm -rf build;md build;cd build;cmake ..;make VERBOSE=1
cd ..;rm -rf build;md build;cd build;cmake ..;make VERBOSE=1

TODO:
1. 测试单目录多执行
2. 测试cario

### 参考
https://cmake.org/cmake/help/latest/guide/tutorial/index.html (cmake官方教程)
https://ninja-build.org/manual.html (ninja文档)
https://zhuanlan.zhihu.com/p/57634435 (x单目录多main，没啥用)