# NodeJS


# Node 核心模块

## Path

1. __dirname: 返回当前执行文件所在的目录（绝对路径形式）。
2. __filename:  返回当前执行文件所在的路径（绝对路径形式）。
3. process.cwd()：返回当前Node进程的文件目录（绝对路径形式）。

1. path.normalize() 将不规范化的路径进行规范化（平台不同规范化的结果也不同）
2. path.join([…paths])方法返回一个拼接好的路径，例如 path.join('/foo', 'bar',);     // return  ‘/foo/bar’
3. path.resolve([…paths]) 该方法将一些的 路径/路径段 解析为绝对路径，从右向左开始拼接路径。如果在处理完所有给定的 path 片段之后，还没有生成绝对路径，则使用当前工作目录。

	总结一下：参数从后向前，若字符以 / 开头，不会拼接到前面的路径；若以 ../ 开头，拼接前面的路径，但是不含前面一节的最后一层路径；若			以 ./ 开头 或者没有符号 则拼接前面路径；

4. path.relative(from, to) 方法根据当前工作目录返回从 from 到 to 的相对路径。 如果 from 和 to 都解析为相同的路径（在分别调   用 path.resolve() 之后），则返回零长度字符串。


## Process(描述当前NodeJS进程的一个信息对象)


## File System(文件系统)

文件操作是开发过程中并不可少的一部分。Node.js 中的 fs 模块是文件操作的封装，它提供了文件读取、写入、更名、删除、遍历目录、链接等 POSIX 文件系统操作。与其它模块不同的是，fs 模块中所有的操作都提供了异步和同步的两个版本,具有 sync 后缀的方法为同步方法，不具有 sync 后缀的方法为异步方法。


文件标识符 flag

1. r：读取
2. w：写入
3. s: 同步
4. +：增加相反操作
5. x：排他方式

**r+ 和 w+ 的区别，当文件不存在时，r+ 不会创建文件，而会抛出异常，但 w+ 会创建文件；如果文件存在，r+ 不会自动清空文件，但 w+ 会自动把已有文件的内容清空。**

### 文件描述符 fd

操作系统会为每个打开的文件分配一个名为文件描述符的**数值**标识，文件操作使用这些文件描述符来识别与追踪每个特定的文件，Window 系统使用了一个不同但概念类似的机制来追踪资源，为方便用户，NodeJS 抽象了不同操作系统间的差异，为所有打开的文件分配了数值的文件描述符。

### 文件操作

#### 常用方法

 1. fs.readFile 方法一次性地异步读取文件内容到内存中
 2.  fs.writeFile 方法一次性地异步将文件内容写到文件中
 3. fs.appendFile 方法以异步的方式将 内容 插入到文件中，如果文件不存在会自动创建
 4. fs.copyFile(src, dest, (err) => {}) 方法以异步的方式将 src的内容 拷贝到 dest 文件中
 5. fs.unlink(filename, callback) 方法删除文件名为 filename 的文件

#### 指定位置读写文件操作
 
 1. fs.open(path[, flags[, mode]], callback) 注意文件标志为flag，默认为 r 。
 2. fs.read(fd, buffer, offset, length, position, callback)
 3. fs.write(fd, buffer, offset, length, position, callback)
 4. fs.close(fd, callback)

#### 目录(文件夹)操作

1. fs.mkdir(path, [options], callback)
2. fs.readdir(path, [options], callback)
3. fs.rmdir(path, callback)



## NodeJS 如何读取超大文件 ？
https://juejin.cn/post/6844903901045456903





