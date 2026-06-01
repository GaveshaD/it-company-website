<template>
  <div class="project-card">
    <h2>{{ title }}</h2>
    <p>{{ description }}</p>
    <span class="category">{{ category }}</span>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  category: String
})
</script>

<style scoped>
.project-card {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}
.category {
  display: inline-block;
  margin-top: 10px;
  padding: 4px 10px;
  background: #2563eb;
  color: rgb(250, 245, 245);
  border-radius: 999px;
  font-size: 14px;
}
</style>