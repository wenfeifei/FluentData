原作者暂时打不开国外博客，协议为MIT协议，源文件 license里面有详情
鉴于codeplex问题，故放在guithub上供大家使用,让更多人知道这个orm
一切权益归原作者所有

FluentData：一种使用Fluent API的新型轻量级ORM模型 
FluentData 是微型 ORM（micro-ORM）家族的一名新成员，旨在比大型 ORM（full ORM）更加易用。它使用 fluent API 并支持 SQL Server、SQL Azure、Oracle 和 MYSQL。 
FluentData 的设计者 Lars-Erik Kindblad 谈到：
	当前市面上的 ORM 框架，如 Entity Framework 和 NHibernate，都过于复杂而且难于学习。此外，由于这些框架自身抽象的查询语言以及从数据库到 .NET 对象的映射太过麻烦，导致它们生成的 SQL 都很低效。 
 FluentData 另辟蹊径，它是一个轻量级框架，拥有简单的 fluent API 并且很容易学会。与其他微型 ORM（如 Dapper 和 Massive）类似，FluentData 关注性能和易用性。它允许开发人员拥有对 SQL 较多的控制，而不是依赖 ORM 进行自动生成。它不仅可以使用 SQL 来执行查询、增添和更新操作，还可以支持使用存储过程和事务。根据文档描述，FluentData 可以在不改动已有结构的情况下，与任何业务对象一同工作。 
 以下是 FluentData 的一些其他特性： 
	· 多结果集（Multiple Result Set）：在一次数据库操作下返回多个数据集； 
　　· 开发人员可使用强类型对象或动态对象； 
　　· 可为创建时需要特殊处理的复杂对象自定义实体工厂（Custom Entity Factory）； 
　　· 具有添加其他数据库支持的能力。 
　　FluentData 需要 .NET 4.0，并支持 SQL Server、SQL Azure、SQL Server Compact 以及使用 .NET 驱动的 Oracle 和 MySQL。 想要了解进一步信息，如代码示例和免费下载，请访问CodePlex 站点上的 FluentData。（http://fluentdata.codeplex.com/）
  
特征
基本特点
支持下列的数据库
MS SQL Server
MS SQL Server 4.0
MS SQL Azure
MS Access
Oracle
MySQL
SQLite
PostgreSQL
IBM DB2
Sybase

使用:
创建连接:
public static IDbContext QueryDB()
{
   return new DbContext().ConnectionStringName(\"testDBContext\", DbProviderTypes.SqlServer);
}
config中的连接字符串实例 
  <connectionStrings>
    <add name="testDBContext" connectionString="server=192.168.1.100;uid=sa;pwd=sa!;database=testDB;" />
  </connectionStrings>
1.需要返回一个实体： 
Product product = QueryDB().Sql(@\"select * from Product where ProductId = 1\").QuerySingle<Product>()

2.根据参数返回一个实体
 Product product = QueryDB().Sql(\"select * from Product where id=@id\").Parameter(\"id\", id).QuerySingle<Product>()
 
3.返回一个泛型。
List<Product> product = QueryDB().Sql("select * from Product where id=@id").Parameter("id", id).Query<Product>();

4.插入操作 
var productId = QueryDB().Insert(\"Product\").Column(\"Name\", \"The Warren Buffet Way\").Column(\"CategoryId\", 1).ExecuteReturnLastId()

也可以这样:var productId = QueryDB().Insert(\"Product\",obj).AutoMap(x => x.Id).ExecuteReturnLastId() 其中ID为自动生成列需要忽略

也可以直接写sql ：var productId = QueryDB().Sql(@"insert into Product(Name, CategoryId) values('The Warren Buffet Way', 1);").ExecuteReturnLastId();

5.修改操作. 
 QueryDB().Update("Product", obj).AutoMap(x => x.Id).Where(x => x.Id).Execute() > 0; 
 
 多个where 可以写成
 QueryDB().Update("Product", obj).AutoMap(x => x.Id).Where(x => x.Id).AndWhere(x=>x.name=="").Execute() > 0; 
 
 参数化:
 QueryDB().Sql(" update Product set IsDelete=1 where id=@id ").Parameter("id", id).Execute() > 0;
 
 使用自定义映射
List<Product> products = Context.Sql(@"select * from Product")
.QueryMany<Product>(Custom_mapper_using_dynamic);

public void Custom_mapper_using_dynamic(Product product, dynamic row)
{
    product.ProductId = row.ProductId;
    product.Name = row.Name;
}

具体使用看参考 :
https://www.cnblogs.com/babietongtianta/p/4365195.html

https://www.cnblogs.com/_popc/archive/2012/12/26/2834726.html 

QQ交流群:180489351


