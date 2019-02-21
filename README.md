# gocrawl
go电影评分爬虫：一个beego框架简单项目，可以深入理解MVC架构
1.beego框架
2.orm和redis进行存储，学会数据交互
3.第三方库如httplib的使用，正则匹配使用等

运行：
bee  run   
浏览器打开：
http://localhost:8080/crawl_moive即可  


登录mysql及 redis查看 相应的数据    

![1](https://github.com/xingyushu/gocrawl/blob/master/img-folder/01.png)


”爬虫“要面对的其实是很多网页和标签的集合 

（1）网页去重   
  哈希存储  布隆过滤器
（2）标签匹配：
   正则表达式
   beautiful soup或lxml这种标签提取库
（3）动态内容：
    phantomjs
    selenium

目标网址：

爬豆瓣电影评分：
https://movie.douban.com/subject/26266893/?from=showing

![2](https://github.com/xingyushu/gocrawl/blob/master/img-folder/02.png)


对应元素正则匹配要写准确：
例如获取导演名称：
  对应正则为：     <a.*?rel="v:directedBy">(.*)</a>
  ```
     reg :=regexp.MustCompile(`<a.*?rel="v:directedBy">(.*?)</a>`)
     result :=reg.FindAllStringSubmatch(movieHtml,-1)
     return string(result[0][1])
  ```  
正则的使用可以参考：  

https://www.cnblogs.com/golove/p/3269099.html
http://www.runoob.com/regexp/regexp-syntax.html
https://www.jianshu.com/p/5285b85654e1

Redis的使用 
https://www.cnblogs.com/zongfa/p/7808807.html

最后登录redis可以查看：

![3](https://github.com/xingyushu/gocrawl/blob/master/img-folder/03.png)

数据库查看：

![4](https://github.com/xingyushu/gocrawl/blob/master/img-folder/04.png)


beego参考文档：
https://beego.me/docs/intro/
