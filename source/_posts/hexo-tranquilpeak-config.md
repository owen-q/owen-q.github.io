---
title: hexo tranquilpeak 설정
date: 2018-06-19 11:57:04
categories:
  - Tech
tags:
  - hexo 
  - blog 
  - seo 
  - 설정 
---

# hexo tranquilpeak 설정하기  
최근 hexo를 사용하여 github.io page를 꾸미던 중에 제대로 된 설정 안내가 없어서 정리해봅니다.
크게 Hexo 설정과, tranquilpeak 테마 설정, disqus 설정을 정리해보겠습니다. 
<hr>

## Hexo 설정 
- plugin 설정 
- _config.yml 작성 


<br/>
#### Plugin 설정 

**hexo-auto-canonical**  

Install 
```
npm install --save hexo-auto-canonical	
```

Setup 
테마path/layout/_partial/header.ejs를 수정한다. 
```
<%- autoCanonical(config, page) %>
```

<br/>
<br/>
** Sitemap **  

Install
```
npm install hexo-generator-seo-friendly-sitemap --save
```

Setup 
theme's _config.yml 
```
sitemap:
    path: sitemap.xml
```


<br/>
<br/>
** rss **  

Install 
```
npm install hexo-generator-feed --save
```

Setup 
theme's _config.yml 
```
feed:
    type: atom
    path: atom.xml
    limit: 20
```

<br/>
<br/>
** robots.txt **  

Install 
```
npm install hexo-generator-robotstxt --save
```

Setup
hexo's _config.yml 
```
robotstxt:
  User-agent: '*'
  Allow: /
  Sitemap: /sitemap.xml
```



<br/>
<br/>
** nofollow **  

Install 
```
npm install hexo-autonofollow --save
```

Setup 
theme's _config.yml 
```
nofollow:
    enable: true
```





<br/>
<br/>
<br/>
<br/>
<hr>

## tranquilpeak 설정 



<br/>
<br/>
<br/>
<br/>
<hr>

## Disqus 설정 
1) Disqus 가입

2) 'I want to install Disqus on my site' 클릭 

3) Website 생성 
  - Website name 기입 
  - Category 설정 

* Website Name에 적은 이름에 따라 input칸 아래에 shortname이 작성된다.
* 이 shortname을 기억해두고 나중에 theme's _config.yml에 적어야한다. 

4) Select a plan 
원하는 plan으로 설정한다.

5) 







