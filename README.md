# Xstore

the localStorage plus tool

### 版本 

  - 1.0
###

### 说明 

  - 此工具是基于localStorage，如浏览器不支持，请勿使用！（呵呵哒，难道还有不支持的？）
  - 原生localStorage仅支持字符串，不支持多种JS类型存储，如对象、数组
  - 原生localStorage不支持过期时间，虽然很多人使用cookie来代替，显然也是一个好方法
  
###

## 使用

* 遵循：一看就懂、傻瓜操作

* 设置存储

```
setStore(key, value, time)
```

* 参数说明：

| 参数名 | 是否必填  | 说明 |
| :-- | :--: | :-- |
| key |   是 | 缓存的key |
|value|   否 | 缓存的内容，为空则值会设置为null，也就是删除  |
|time |   否 | 过期时间，单位：秒；若为null则表示永不过期，若为-1则表示将其缓存立刻设置为过期但保留缓存值的内容  |
	
* 亮点（坑）：

1. 缓存的key，支持'foo.bar.baz'的形式存储

2. 虽然支持`foo.bar.baz`的形式存储，但是如果`foo.bar`没有设置或者之前缓存的类型为字符串，则`foo.bar.baz`无法设置成功

3. 若一开始没有设置`foo`的缓存内容且此内容不是对象，则无法设置`foo.bar`，以此类推，必须上一层先设置了才能设置下一层这个bug会在下一个版本（2.0）中得到解决

4. 缓存值不支持函数类型，这里吹牛吹大了，以为什么类型都能支持，但是不支持函数类型，呵呵哒，这个也会在下一个版本（2.0）解决

5. 过期时间，这个的坑不大，很好，唯一一个设计还算合理的地方

* 获取缓存

```
getStore(name)
```

同样支持'foo.bar.baz'形式，这个基本没坑还有亮点：会自动判断缓存是否过期，如果缓存已经过期则会返回null

* 删除缓存

```
removeStore(name)
```

