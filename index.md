---
layout: default
title: 我的博客
background: /assets/images/bg.jpg  # 背景图路径
---

<style>
  /* 全屏背景图+半透明遮罩 */
  body {
    background: url('{{ page.background }}') no-repeat center fixed;
    background-size: cover;
    margin: 0;
    padding: 0;
  }
  .content-box {
    background-color: rgba(255, 255, 255, 0.85);
    max-width: 900px;
    margin: 2rem auto;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }
  /* 导航样式 */
  .nav {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    margin-bottom: 2rem;
  }
  .nav a {
    color: #333;
    text-decoration: none;
    font-weight: 600;
    padding: 0.3rem 0;
    border-bottom: 2px solid transparent;
    transition: all 0.3s;
  }
  .nav a:hover {
    border-color: #0066cc;
  }
  /* 文章列表样式 */
  .post-list {
    list-style: none;
    padding: 0;
  }
  .post-item {
    margin-bottom: 1.5rem;
    padding-bottom: 1rem;
    border-bottom: 1px dashed #ddd;
  }
  .post-title {
    font-size: 1.2rem;
    color: #222;
    margin-bottom: 0.3rem;
  }
  .post-date {
    color: #666;
    font-size: 0.9rem;
  }
</style>

<div class="content-box">
  <!-- 导航菜单 -->
  <nav class="nav">
    <a href="/">首页</a>
    <a href="/about">关于</a>
    <a href="/tags">标签</a>
    <a href="/archive">归档</a>
  </nav>

  <!-- 最新文章列表 -->
  <h1>最新文章</h1>
  <ul class="post-list">
    {% for post in site.posts limit:5 %}
      <li class="post-item">
        <a href="{{ post.url }}" class="post-title">{{ post.title }}</a>
        <div class="post-date">
          {{ post.date | date: "%Y年%m月%d日" }} · 阅读约需 {{ post.content | reading_time }}分钟
        </div>
        <p>{{ post.excerpt | strip_html | truncate: 100 }}</p>
      </li>
    {% endfor %}
  </ul>

  <!-- 查看更多按钮 -->
  <div style="text-align: center; margin-top: 2rem;">
    <a href="/archive" class="button">查看全部文章 →</a>
  </div>
</div>
