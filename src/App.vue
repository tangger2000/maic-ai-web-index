<script setup>
import DocsViewer from './components/DocsViewer.vue'

const softwares = [
  { name: 'MAIC 大模型客户端', description: '材料科学智能体运行环境', link: '#' },
  { name: 'AI 协作工具', description: '团队协作与知识管理的人工智能工具', link: '#' },
  { name: '图像生成器', description: '基于生成式模型的图片创作软件', link: '#' },
  { name: '语音识别助手', description: '提供语音转文字及翻译功能', link: '#' },
]
</script>

<template>
  <main id="app">
    <header class="hero">
      <h1>MAIC 软件中心</h1>
      <p>下载 MAIC 大模型客户端和相关工具</p>
    </header>
    <ul class="software-list">
      <li v-for="item in softwares" :key="item.name" class="software-item">
        <h2>{{ item.name }}</h2>
        <p>{{ item.description }}</p>
        <a :href="item.link" class="download">下载</a>
      </li>
    </ul>

    <DocsViewer />
  </main>
</template>

<style scoped>
.software-list {
  list-style: none;
  padding: 0;
}
.hero {
  background: linear-gradient(135deg, #42b883, #2c3e50);
  color: #fff;
  padding: 2rem;
  border-radius: 8px;
  margin-bottom: 2rem;
}
.software-item {
  border: 1px solid #ccc;
  border-radius: 8px;
  margin: 1rem 0;
  padding: 1rem;
}
.download {
  display: inline-block;
  margin-top: 0.5rem;
  color: #fff;
  background-color: #42b883;
  padding: 0.4rem 0.8rem;
  border-radius: 4px;
}
.download:hover {
  background-color: #2c8c68;
}

.docs {
  margin-top: 3rem;
}
</style>
