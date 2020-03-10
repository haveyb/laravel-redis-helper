Laravel 框架使用 Redis 辅助文件

　　由于Laravel 中使用 redis 采用的是门面模式，并且引用的是phpredis，在Laravel 框架中并没有redis的相关方法，这样就导致对于 Redis 操作不熟悉的人，可能就不知道都有什么命令，该如何操作了。

　　该composer包 基于此开发，对redis的所有方法进行了分类封装和解释，使得不熟悉redis的开发者也能很轻松的使用，同样也可以看源码中对每个redis命令的解释，加深对redis命令的掌握。

以下是几个使用示例：

```
RedisHelper::set('zz', 'hello world');
```
```
RedisHelper::get('age');
```

```
RedisHelper::mget(['age', 'username', 'sex'])
```

```
RedisHelper::sInterStore(['aa', 'bb'])
```

下面是部分源代码

```
/**
     * 删除指定的键
     *
     * @param $param string|array
     * @return int 被删除的键的数目（有不存在的键，不影响其他存在的键的删除）
     * RedisHelper::del('age')
     * RedisHelper::del(['city', 'username', 'sex'])
     */
    public static function del($param)
    {
        return Redis::del($param);
    }

    /**
     * 如果键不存在，就设置键值（如果键已经存在了，则不再设置，返回false）
     *
     * @param $key
     * @param $value
     * @return  bool
     */
    public static function setNx($key, $value)
    {
        return Redis::setnx($key, $value);
    }
```

@website https://www.haveyb.com
cyf
