---
title: 
date: 2021-11-15 00:00:00
comments: false
permalink: /404.html
top_img: false
aside: false
---

<p align="center"><font size=5>
404 Page Not Found<br>
Woops 这个页面被 404 猫猫叼走惹<br>
可能这个页面链接语法有问题，或者已被删除<br>
<font color=orange>网站内容已更新，所有的页面已迁移，请使用搜索功能</font><br>
404 猫猫将会在 <span id="timeout">15</span>s 后带你回到首页<br>
当然，你可以 <strong><a href=" / " data-pjax-state>直接点这里</a> 来返回首页

</font></p>
<script>
let countTime = 15;

function count() {

  document.getElementById('timeout').textContent = countTime;
  countTime -= 1;
  if(countTime === 0){
    location.href = '/';
  }
  setTimeout(() => {
    count();
  }, 1000);
}

count();
</script>

![404 Page Not Found](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Blog/404Page.jpg)