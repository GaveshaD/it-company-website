<template>
  <div class="project-card" :class="category.toLowerCase()">
    <h2 v-html="highlightedTitle || title"></h2>
    <p>{{ description }}</p>
    <span class="category" :class="category.toLowerCase()">{{ category }}</span>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  highlightedTitle: String,
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
.project-card:active {
  transform: scale(0.98);
}
.category {
  display: inline-block;
  margin-top: 10px;
  padding: 4px 10px;
  border-radius: 999px;
  font-size: 14px;
  color: white;
}

.category.web {
  background: #2563eb;
}

.category.mobile {
  background: #16a34a;
}

.category.cloud {
  background: #9333ea;
}
.project-card.web {
  border-top: 4px solid #2563eb;
}

.project-card.mobile {
  border-top: 4px solid #16a34a;
}

.project-card.cloud {
  border-top: 4px solid #9333ea;
}
</style>