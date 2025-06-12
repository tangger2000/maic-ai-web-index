<script setup>
import { ref, onMounted } from 'vue'
import { marked } from 'marked'

const docs = ref([])

const modules = import.meta.glob('../docs/*.md', { as: 'raw' })

async function loadDocs() {
  const entries = Object.entries(modules)
  entries.sort((a, b) => a[0].localeCompare(b[0], undefined, { numeric: true }))
  for (const [path, loader] of entries) {
    const content = await loader()
    docs.value.push({ title: extractTitle(content), html: marked.parse(content) })
  }
}

function extractTitle(content) {
  const match = content.match(/^#\s+(.*)/)
  return match ? match[1] : '文档'
}

onMounted(loadDocs)
</script>

<template>
  <section class="docs">
    <article v-for="(doc, index) in docs" :key="index" class="doc-item">
      <h2>{{ doc.title }}</h2>
      <div v-html="doc.html" />
    </article>
  </section>
</template>

<style scoped>
.docs {
  max-width: 800px;
  margin: 2rem auto;
  text-align: left;
}
.doc-item + .doc-item {
  margin-top: 2rem;
  padding-top: 1rem;
  border-top: 1px solid #ddd;
}
</style>
