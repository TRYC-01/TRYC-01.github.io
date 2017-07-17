---
layout: post
date: 2017-6-20 22:38:20 +0800
title: jekyll分页实现
categories: jekyll
---

 对于大多数网站（尤其是博客），当文章越来越多时，就会有分页显示文章列表的需求。jekyll已经自建分页功能，我们只需要根据约定放置文件即可
 
 在jekyll3中，需要在gems中安装 jekyll-paginate 插件，并添加到Gemfile和 _config.yml中。在Jekyll2中，分页是标准功能。
 
 分页功能只支持HTML文件

* 安装jekyll-paginate

  ![]({{site.url}}/assets/images/install jekyll-paginate.jpg)

* 添加到Gemfile

  ![]({{site.url}}/assets/images/paginate in Gemfile.jpg)

* 添加到_config.yml,且设置paginate 和 paginat_path: "

  ![]({{site.url}}/assets/images/paginate in config.yml.jpg)

# 生成带有分页功能的文章

  ![]({{site.url}}/assets/images/paginate code1.jpg)
  ![]({{site.url}}/assets/images/paginate code2.jpg)

***
## 可用的Liquid属性
  分页功能插件使paginator liquid对象具有以下属性：
> page   当前页码
> 
> per_page  每页文章数量
> 
> posts     当前页面文章列表
> 
> total_posts 总文章数
> 
> total_pages 总页数
> 
> previous_page 上一页码或nil
> 
> previous_page_path 上一页路径或nil
> 
> next_page 下一页码或nil
> 
> next_page_path 下一页路径或nil