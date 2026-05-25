<template>
  <div class="card">
    <div class="icon">{{ icon }}</div>

    <h2>{{ title }}</h2>

    <p>{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  icon: String,
  title: String,
  description: String
})
</script>

<style scoped>
.card {
  background: white;
  padding: 25px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

.card h2 {
  margin-bottom: 10px;
  color: #222;
}

.card p {
  color: #555;
  line-height: 1.5;
}

.icon {
  font-size: 48px;
  margin-bottom: 20px;
}
</style>