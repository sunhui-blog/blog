---
title: mysql
date: 2021-03-04 13:34:43
tags: 数据库
categories: 数据库
---
<style type="text/css">
.red{color:red;}
</style>

<p>数据库常用sql整理。</p>

<!--more-->
<ol>
  <li>创建数据库:
    ```
    CREATE DATABASE <数据库名>;

    // 创建notebook数据库
    mysql> CREATE DATABASE notebook;
    ```
  </li>
  <li>显示数据库列表:
    ```
    SHOW DATABASES;

    mysql> SHOW DATABASE;
    ```
  </li>
  <li>显示库中的数据表:
    ```
    SHOW TABLES;

    mysql> SHOW TABLES;
    ```
  </li>
  <li>选择数据库:
    ```
    use <数据库名>;

    // 选择notebook数据库
    use notebook;
    ```
  </li>
  <li>删除数据库:
    ```
    DROP DATABASE <数据库名>;

    // 删除notebook数据库
    mysql> DROP DATABASE notebook;
    ```
  </li>
  <li>创建数据表:
    ```
    CREATE TABLE <数据表名> (column_name column_type);
    ```
  </li>
  <li>显示表中的记录:
    ```
    SELECT * FROM <数据表名>;
    ```
  </li>
  <li>删除数据表数据:
    ```
    DELETE FROM <数据表名>;
    ```
  </li>
  <li>删除数据表:
    ```
    DROP TABLE <数据表名>;
    ```
  </li>
  <li>删除单条数据:
    ```
    DELETE FROM <数据表名> WHERE <参数名> = <参数值>;
    ```
  </li>
  <li>查询数据:
    ```
    SELECT * FROM <数据表名>;
    ```
  </li>
  <li>排序(ASC或DESC-升序或降序):
    ```
    SELECT * from <数据表名> ORDER BY <参数名> ASC;
    ```
  </li>
  <li>查看表结构:
    ```
    show columns from <数据表名>;
    ```
  </li>
</ol>

<p style="margin-top: 20px;">常见的数据模型有<span class="red">层次模型</span>、<span class="red">网状模型</span>和<span class="red">关系模型</span>三种。</p>

<p>需要关注问题：最新的加密方式node还不支持，具体版本是哪一版本，具体不能加密的原因是什么？</p>

<h4 style="margin-top: 40px;"><附></h4>
<ol>
  <li>
    管理MySQL：https://www.liaoxuefeng.com/wiki/1177760294764384/1246617774585536
  </li>
  <li>
    数据库设计：https://taogenjia.com/2019/11/13/database-system-3-database-design/
  </li>
</ol>
