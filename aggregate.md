db.collection.aggregate(pipeline, options);

pipeline Array

# 与mysql中的字段对比说明
$project # 返回哪些字段,select,说它像select其实是不太准确的,因为aggregate是一个阶段性管道操作符,$project是取出哪些数据进入下一个阶段管道操作,真正的最终数据返回还是在group等操作中;

$match # 放在group前相当于where使用,放在group后面相当于having使用

$sort # 排序1升-1降 sort一般放在group后,也就是说得到结果后再排序,如果先排序再分组没什么意义;

$limit # 相当于limit m,不能设置偏移量

$skip # 跳过第几个文档

$unwind # 把文档中的数组元素打开,并形成多个文档,参考Example1

$group: { _id: <expression>, <field1>: { <accumulator1> : <expression1> }, ...  
# 按什么字段分组,注意所有字段名前面都要加$,否则mongodb就为以为不加$的是普通常量,其中accumulator又包括以下几个操作符
# $sum,$avg,$first,$last,$max,$min,$push,$addToSet
#如果group by null就是 count(*)的效果

$geoNear # 取某一点的最近或最远,在LBS地理位置中有用

$out # 把结果写进新的集合中。注意1,不能写进一个分片集合中。注意2,不能写进

