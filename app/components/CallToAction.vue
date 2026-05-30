<template>
  <section class="cta">
    <h2>{{ title }}</h2>
    <p>{{ description }}</p>

    <NuxtLink :to="buttonLink" class="cta-button">
      {{ buttonText }}
    </NuxtLink>
  </section>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  buttonText: String,
  buttonLink: String
})
</script>

<style scoped>
.cta {
  text-align: center;
  padding: 80px 20px;
  border-radius: 20px;
  background: linear-gradient(to right, #0f172a, #1e3a8a);
  color: white;
}

.cta-button {
  display: inline-block;
  margin-top: 20px;
  padding: 12px 24px;
  background: #2563eb;
  color: white;
  text-decoration: none;
  border-radius: 8px;
}
</style>