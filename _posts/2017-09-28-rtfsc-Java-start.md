---
layout: post
title: JDBC中execute、executeQuery和executeUpdate的区别
categories: Java
description:  JDBC中execute、executeQuery和executeUpdate的区别
keywords: JDBC MySQL
---

Statement 接口提供了三种执行 SQL 语句的方法：executeQuery、executeUpdate 和 execute。使用哪一个方法由 SQL 语句所产生的内容决定。

**1.方法executeQuery** 
 用于产生单个结果集（ResultSet）的语句，例如 SELECT 语句。 被使用最多的执行 SQL 语句的方法。这个方法被用来执行 SELECT 语句，它几乎是使用最多的 SQL 语句。但也只能执行查询语句，执行后返回代表查询结果的ResultSet对象。
如：

//加载数据库驱动

Class.forName("com.MySQL.jdbc.Driver");

//使用DriverManager获取数据库连接
Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/test",
                "root","1234");

//使用Connection来创建一个Statment对象
Statement  stmt = conn.createStatement();

//执行查询语句
ResultSet rs =stmt.executeQuery("select * from teacher");

//把查询结果输出来

while (rs.next())
{
    System.out.println(rs.getInt(1) + "/t" +    rs.getString(2)); 
}

**2.方法executeUpdate**
用于执行 INSERT、UPDATE 或 DELETE 语句以及 SQL DDL（数据定义语言）语句，例如 CREATE TABLE 和 DROP TABLE。INSERT、UPDATE 或 DELETE 语句的效果是修改表中零行或多行中的一列或多列。executeUpdate 的返回值是一个整数（int），指示受影响的行数（即更新计数）。对于 CREATE TABLE 或 DROP TABLE 等不操作行的语句，executeUpdate 的返回值总为零。

如：

//加载数据库驱动

Class.forName("com.mysql.jdbc.Driver");

//使用DriverManager获取数据库连接

Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/test",
                "root","1234");

//使用Connection来创建一个Statment对象

Statement  stmt = conn.createStatement(); 
//执行DML语句，返回受影响的记录条数

return stmt.executeUpdate(sql);

**3.方法execute：** 
    可用于执行任何SQL语句，返回一个boolean值，表明执行该SQL语句是否返回了ResultSet。如果执行后第一个结果是ResultSet，则返回true，否则返回false。但它执行SQL语句时比较麻烦，通常我们没有必要使用execute方法来执行SQL语句，而是使用executeQuery或executeUpdate更适合，但如果在不清楚SQL语句的类型时则只能使用execute方法来执行该SQL语句了。
如：  //加载驱动

            Class.forName(driver);

         //获取数据库连接

            conn = DriverManager.getConnection(url , user , pass); 
            //使用Connection来创建一个Statment对象 
            stmt = conn.createStatement();
            //执行SQL,返回boolean值表示是否包含ResultSet 
            boolean hasResultSet = stmt.execute(sql); 
            //如果执行后有ResultSet结果集

            if (hasResultSet)

            {

                //获取结果集 
                rs = stmt.getResultSet();

                //ResultSetMetaData是用于分析结果集的元数据接口 
                ResultSetMetaData rsmd = rs.getMetaData();

                int columnCount = rsmd.getColumnCount();
                //迭代输出ResultSet对象

                while (rs.next())

                {//依次输出每列的值
                    for (int i = 0 ; i < columnCount ; i++ ) 
                    {

                        System.out.print(rs.getString(i + 1) + "/t");

                    }
                    System.out.print("/n");

                } 
            }

            else 
            {

                System.out.println("该SQL语句影响的记录有" + stmt.getUpdateCount() + "条");
            } 
内容决定。

