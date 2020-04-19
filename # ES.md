# ES

* 需要jdk1.8以上，在bin目录下启动es服务

* 访问 http://localhost:9200/   启动成功

* es的图形化界面 elasticsearch-head-master 需要node.js

  ```
  图形化界面 的安装
  node -v
  D:\ES\elasticsearch-head-master>grunt server
  
  1. D:\ES\elasticsearch-head-master>npm install -g grunt-cli
  2. D:\ES\elasticsearch-head-master>npm install
  3. D:\ES\elasticsearch-head-master>grunt server 
  http://localhost:9100/
  ```

* 解决es跨域不能访问的问题 修改config/elasticsearch.yml

```
http.cors.enabled: true
http.cors.allow-origin: "*"
```

* ```
  mysql databases -->tables-->rows-->columns
  Elasticsearch index -->types-->documents-->fields
  ```

* ```json
  {
      "mappings":{
          "article":{ //types 
              "properties":{//属性 document
                  "id":{  //字段
                      "type":"long",
                      "store": true
                  },
                  "title":{
                      "type":"text",
                      "store":true,
                      "index":true,
                      "analyzer":"standard"
                  },
                   "content":{
                      "type":"text",
                      "store":true,
                      "index":true,
                      "analyzer":"standard"
                  }
              }
          }
      }
  }
  ```

* ```
  http://127.0.0.1:9200/blog1/article/1
  blog1 -->索引库  article -->type  1-->_id 文档的主键
  ```

* ES 修改的本质还是先删除，在添加

* ```json
  http://127.0.0.1:9200/blog/hello/_search
  query 不带分词器的查询
  {
  	"query":{
  		"term":{
  			"title":"文"//字段的名
  		}
  	}
  }
  ```

* ```json
  http://127.0.0.1:9200/blog/hello/_search
  queryString  带分词器的查询 标准分词，一个汉字一个词
  {
  	"query":{
  		"query_string":{
  			"default_field":"title",
  			"query":"文档"
  		}
  	}
  }
  ```

* ES集群

```
索引库分片 默认是5片
复制ES文件时data目录不能有

在elasticsearch.yml中添加集群的配置后，直接启动ES，会自动形成集群，使用es-heard来查看各个节点

```

