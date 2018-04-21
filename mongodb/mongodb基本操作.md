
以下都针对mydb数据库和test collection

   > mongodb 安装
	brew install mongodb
    mongodb连接
    mongod 开启服务器
    mongo 连接默认数据库test
    mongo ip/mydb 连接ip的mydb数据库；
    
### 使用或创建库    
   > use mydb 使用或创建数据库mydb   
    注：没有数据的数据库是查不到的
    
### 删库    
   >  db.dropDatabase();删除正在使用的数据库
   
### 添加文档。系统并自动创建了mydbcollection
   > db.mydb.insert({“name”,”123”})
### 创建集合   
   >db.createCollection(“test”,{ capped : true, autoIndexId : true, size : 
                                  6142800, max : 10000 } )                             
     capped ：true 则表示固定大小的collection，超过的文档就覆盖之前的文档
     autoIndexId：true 则表示设置_id创建索引 默认false
     size：collection的大小
     max：collection允许的最大文档数
    其实没有创建collection，mongodb也会创建
   > 在 MongoDB 中，你不需要创建集合。当你插入一些文档时，MongoDB 会自动创建集合。
    > db.mycol2.insert({"name" : "菜鸟教程"})
    > show collections
    mycol2
    
#### 删除集合    
    db.mycol2.drop();

#### 添加文档
   > db.col.insert({title: 'MongoDB 教程', 
        description: 'MongoDB 是一个 Nosql 数据库',
        by: '菜鸟教程',
        url: 'http://www.runoob.com',
        tags: ['mongodb', 'database', 'NoSQL'],
        likes: 100
    })   
    
    
   也可以包装成对象
   
   > document=({title: 'MongoDB 教程', 
       description: 'MongoDB 是一个 Nosql 数据库',
       by: '菜鸟教程',
       url: 'http://www.runoob.com',
       tags: ['mongodb', 'database', 'NoSQL'],
       likes: 100
   });
   执行后显示结果如下：
   {
           "title" : "MongoDB 教程",
           "description" : "MongoDB 是一个 Nosql 数据库",
           "by" : "菜鸟教程",
           "url" : "http://www.runoob.com",
           "tags" : [
                   "mongodb",
                   "database",
                   "NoSQL"
           ],
           "likes" : 100
   }
   执行插入操作：
   > db.col.insert(document)
   WriteResult({ "nInserted" : 1 })
   >也可以使用db.col.save(document)，显示信息会更详细
   mongodb3.4后添加了单条插入和多条插入方法
    db.col.insertOne(document)
    db.col.insertMany(document)
    
### save方法比insert方法更强大
   > 反馈更明显，如果也可以作为修改
    
### 单条修改文档
   >db.col.update({'title':'MongoDB 教程'},{$set:{'title':'MongoDB'}})
    WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })   # 输出信息
   > db.col.find().pretty()
    {
            "_id" : ObjectId("56064f89ade2f21f36b03136"),
            "title" : "MongoDB",
            "description" : "MongoDB 是一个 Nosql 数据库",
            "by" : "菜鸟教程",
            "url" : "http://www.runoob.com",
            "tags" : [
                    "mongodb",
                    "database",
                    "NoSQL"
            ],
            "likes" : 100
    }
    >
    注：这样只会更新匹配到的第一条
    db.collection.update(
       <query>,
       <update>,
       {
         upsert: <boolean>,
         multi: <boolean>,
         writeConcern: <document>
       }
    )
    参数说明：
    query : update的查询条件，类似sql update查询内where后面的。
    update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
    upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
    multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
    writeConcern :可选，抛出异常的级别。
    
   > db.test_collection.updateOne({"name":"abc"},{$set:{"age":"28"}})
    { "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }
    > db.test_collection.find()
    { "_id" : ObjectId("59c8ba673b92ae498a5716af"), "name" : "abc", "age" : "28", "status" : "zxc" }
    { "_id" : ObjectId("59c8ba673b92ae498a5716b0"), "name" : "dec", "age" : "19", "status" : "qwe" }
    { "_id" : ObjectId("59c8ba673b92ae498a5716b1"), "name" : "asd", "age" : "30", "status" : "nmn" }
    >
    更新多个文档
    > db.test_collection.updateMany({"age":{$gt:"10"}},{$set:{"status":"xyz"}})
    { "acknowledged" : true, "matchedCount" : 3, "modifiedCount" : 3 }
    > db.test_collection.find()
    { "_id" : ObjectId("59c8ba673b92ae498a5716af"), "name" : "abc", "age" : "28", "status" : "xyz" }
    { "_id" : ObjectId("59c8ba673b92ae498a5716b0"), "name" : "dec", "age" : "19", "status" : "xyz" }
    { "_id" : ObjectId("59c8ba673b92ae498a5716b1"), "name" : "asd", "age" : "30", "status" : "xyz" }
    >
#### 多条修改文档
   >db.col.update({'title':'MongoDB 教程'},{$set:{'title':'MongoDB'}},{multi:true})
    
#### 删除文档
  > db.inventory.deleteMany({})
  删除 status 等于 A 的全部文档：
  db.inventory.deleteMany({ status : "A" })
  删除 status 等于 D 的一个文档：
  db.inventory.deleteOne( { status: "D" } )