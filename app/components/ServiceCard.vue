<template>
  <div class="card">
    <div class="icon">{{ icon }}</div>
    <h2>{{ title }}</h2>
    <p>{{ description }}</p>

    <span
      class="service-category"
      :class="category.toLowerCase()"
    >
      {{ category }}
    </span>
  </div>
</template>

<script setup>
defineProps({
  icon: String,
  title: String,
  description: String,
  category: String
})
</script>

<style scoped>
.card {
  background: white;
  padding: 25px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card h2 {
  margin-bottom: 10px;
  color: #222;
}

.card p {
  color: #555;
  line-height: 1.5;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}
.icon {
  font-size: 32px;
  margin-bottom: 10px;
}
.service-category {
  display: inline-block;
  margin-top: 10px;
  padding: 4px 10px;
  border-radius: 999px;
  background: #2563eb;
  color: white;
  font-size: 12px;
}
.service-category {
  display: inline-block;
  margin-top: 10px;
  padding: 4px 10px;
  border-radius: 999px;
  color: white;
  font-size: 12px;
}

.service-category.web {
  background: #2563eb;
}

.service-category.mobile {
  background: #16a34a;
}

.service-category.cloud {
  background: #9333ea;
}
</style>