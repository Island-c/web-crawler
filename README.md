## 爬取凤凰网新闻

#### 爬虫框架

   通常爬虫分为五个部分，分别为：爬虫调度器、URL管理器、网页下载器、网页解析器与数据存储器。

（一）URL管理器

该模块主要维护两个变量：以爬取的URL集合和未爬取的URL集合。之所以选择集合是因为集合中元素不能重复的特点，这就给url进行了一个去重。

- 该模块的主要接口有：
    - 判断是否有待取的URL，方法定义为has_new_url()。
    - 添加新的URL到未爬取的集合中，方法定义为：add_new_url(url),add_new_urls(urls)。
    - 获取未爬取的URL，方法定义为get_new_url()。
    - 获取未爬取的URL集合大小，方法定义为new_url_size()。
    - 获取已爬取的URL集合大小，方法定义为old_url_size()。

（二）网页下载器

        该模块主要用到的库为requests，当然大家也可以根据自己需要选择urllib库等。具有的接口为：download（url）。

（三）网页解析器

        用于解析的库主要用到BeautifulSoup、lxml等。提供一个parser对外的接口。

（四）数据存储器

        数据存储器主要包括两个方法：store_data(data)用于将解析出来的有效数据存储到内存；output_html()用于将存储的数据输出到指定的文件或者数据库。

（五）爬虫调度器

​	该模块首先要初始化其他四个模块，通过crawl(root_url)方法将起始链接传入URL管理器，然后按照调度器流程执行各个模块，协调工作。

