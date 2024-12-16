
推荐一个介轻量ORM和全功能ORM的开源项目。


# 01 项目简介


RepoDB 提供了基本操作所需的方法，同时也提供了一些高级功能，如第二层缓存、跟踪、仓储、属性处理器和批量/大量操作。支持的数据库，包括SqlServer、SQLite、MySql和PostgreSql等。


# 02 关键特性


**1、基础操作支持**


RepoDB提供了执行基础数据库操作（如CRUD操作）所需的初步方法。


**2、高级特性**


第二层缓存：用于提高数据检索效率。


跟踪：用于监控和记录数据库操作。


仓储：用于封装数据库访问逻辑。


属性处理器：用于自定义属性映射和转换。


批量/大量操作：用于高效处理大量数据。


**3、开发简单易用**


使用RepoDB时，开发者用极少的代码调用高级操作。


**4、批量操作与数据模型同步**


在执行批量操作（如BulkInsert和BulkMerge）时，RepoDB会在执行后将生成的标识列（identity columns）值设置回数据模型，满足开发者重要用例需求。


**5、多种执行方式支持**


支持不同的执行方式，包括原子（atomic）、批处理（batch）和批量（bulk）操作。


# 03 使用方法


**1、插入记录**



```
//插入单条记录
var person = new Person
{
    Name = "John Doe",
    Age = 54,
    CreatedDateUtc = DateTime.UtcNow
};
using (var connection = new SqlConnection(ConnectionString))
{
    var id = connection.Insert(person);
}

//插入多条记录
var people = GetPeople(100);
using (var connection = new SqlConnection(ConnectionString))
{
    var rowsInserted = connection.InsertAll(people);
}

```

**2、查询记录**



```
//查询单条记录
using (var connection = new SqlConnection(ConnectionString))
{
    var person = connection.Query(e => e.Id == 10045);
}

//查询多条记录
using (var connection = new SqlConnection(ConnectionString))
{
    var people = connection.QueryAll();
}

```

**3、更新记录**



```
//更新单条记录
var person = new Person
{
    Id = 1,
    Name = "James Doe",
    Age = 55,
    DateInsertedUtc = DateTime.UtcNow
};
using (var connection = new SqlConnection(ConnectionString))
{
    var updatedRows = connection.Update(person);
}

//更新多条记录
var people = GetPeople(100);
people
    .AsList()
    .ForEach(p => p.Name = $"{p.Name} (Updated)");
using (var connection = new SqlConnection(ConnectionString))
{
    var updatedRows = connection.UpdateAll(people);
}

```

**4、删除记录**



```
//删除单条记录
using (var connection = new SqlConnection(ConnectionString))
{
    var deletedRows = connection.Delete(10045);
}

//删除多条记录
using (var connection = new SqlConnection(ConnectionString))
{
    var deletedRows = connection.DeleteAll();
}

```

# 04 项目地址


[https://github.com/mikependon/RepoDB](https://github.com)


\- End \-


**更多开源项目请查看**：[一个专注推荐优秀.Net开源项目的榜单](https://github.com)


推荐阅读


[2个零基础入门框架教程！](https://github.com)


[一款可以替代Navicat的数据库管理工具](https://github.com):[豆荚加速器官网PodHub](https://doujiaa.com)


[CSCore：一个.Net功能强大且灵活的开源音频处理库](https://github.com)


[Blazor开源UI简洁组件：10个热门.Net开源项目推荐！](https://github.com)


[ExcelDataReader：一个.Net高性能Excel开源读取器](https://github.com)


