---


categories:

- 教程

cover: >-

[https://ik.imagekit.io/nicexl/Wallpaper/b6edd017c2d2eca2.webp?ik-sdk-version=javascript-1.4.3&updatedAt=1661082299520](https://ik.imagekit.io/nicexl/Wallpaper/b6edd017c2d2eca2.webp?ik-sdk-version=javascript-1.4.3&updatedAt=1661082299520)

date: '2022-08-21 18:13:03'

tags:
- Hexo

title: 随机访问博客文章

abbrlink: '2377'

---

## 前沿

此教程是根据 js 实现的随机访问博客文章

部署难度：简单

## 正文

在博客根目录新建`{blogroot}/scripts/random.js`

```random.js
/ *随机文章 /

hexo.extend.generator.register('random', function (locals) {
  const config = hexo.config.random || {}
  const posts = []
  for (const post of locals.posts.data) {
    if (post.random !== false) posts.push(post.path)
  }
  return {
    path: config.path || 'random/index.html',
    data: `<html><head><script>var posts=${JSON.stringify(posts)};window.open('/'+posts[Math.floor(Math.random() * posts.length)],"_self")</script></head></html>`
  }
})
```

访问 yourdomain.com/random，就会发现，会随机转跳到一篇博客文件。

#### Done

[random](https://xlenco.eu.org/random)