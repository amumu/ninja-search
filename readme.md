ninja-search
===

[shixiz.com](http://shixiz.com)   

wiki
-----
* [Home Page](https://github.com/dbbbit/ninja-search/wiki)

* [Search Api](https://github.com/dbbbit/ninja-search/wiki/Search-Api)

require:
--------

* flask
* mongodb  
* [elasticsearch](http://www.elasticsearch.org/overview/elasticsearch/) + [ik分词插件](https://github.com/medcl/elasticsearch-analysis-ik)
* [v2ex_scrapy](https://github.com/dbbbit/v2ex_scrapy) 

python package
--------------

    sudo pip install -r requirements.txt


elasticsearch 配置
-------------------

* [安装 ik 分词](https://github.com/medcl/elasticsearch-analysis-ik)

* 在 esroot /config /elasticsearch.yml 添加以下内容：

        #: 启用 ES 动态脚本,以提供综合排序
        script.disable_dynamic: false


爬取数据
--------

* [见 v2ex_scrapy 说明](https://github.com/dbbbit/v2ex_scrapy)


索引
--------

* ElasticSearch Scheme Mapping  

        sh ninja-search/deploy/mapping_ik.sh

* 手动创建 Mongo 索引

        db.reply.createIndex({topic_id:1})

* 索引数据
    
        deploy/mongo2es.py 
    
* 将线上索引指向新的索引
    
        sh deploy/alias_v2_ik.sh


Run 
----
  
    sudo python index.py






