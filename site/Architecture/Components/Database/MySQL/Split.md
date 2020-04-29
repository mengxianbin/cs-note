[Home](https://mengxianbin.github.io) /
[cs-notes](https://mengxianbin.github.io/cs-notes/site) /
[Architecture](https://mengxianbin.github.io/cs-notes/site/Architecture) /
[Components](https://mengxianbin.github.io/cs-notes/site/Architecture/Components) /
[Database](https://mengxianbin.github.io/cs-notes/site/Architecture/Components/Database) /
[MySQL](https://mengxianbin.github.io/cs-notes/site/Architecture/Components/Database/MySQL) /
[Split](https://mengxianbin.github.io/cs-notes/site/Architecture/Components/Database/MySQL/Split)

# 切分

## 水平切分

* Sharding
* 结构不变，按行拆分

## 垂直切分

* 按列拆分

---

## Sharding 策略

* 哈希取模： hash(key) % N
* 范围：ID 范围 / 时间范围 
* 映射表：使用单独库存储映射关系

## Sharding 问题

* 事务
    * 分布式事务
        * 如 XA 接口
* 连接
    * 将原连接分解成多个单表查询
    * 在用户程序中连接
* ID 唯一性
    * 全局唯一 ID （GUID）
    * 每个分片指定一个 ID 范围
    * 分布式 ID 生成器
        * Twitter - Snowflake

---