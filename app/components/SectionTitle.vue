<template>
  <div class="section-title">
    <h1>{{ title }}</h1>

    <p>{{ subtitle }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  subtitle: String
})
</script>

<style scoped>
.section-title {
  text-align: center;
  margin-bottom: 60px;
}

.section-title h1 {
  font-size: 48px;
  margin-bottom: 15px;
}

.section-title p {
  color: #666;
  font-size: 18px;
}
</style>