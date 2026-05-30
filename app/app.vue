<template>
  <div :class="{ dark: isDark }">
    <Navbar />

    <button @click="isDark = !isDark">
      {{ isDark ? "☀️ Light Mode" : "🌙 Dark Mode" }}
    </button>

    <div class="container">
      <NuxtPage />
    </div>

    <FooterSection />
  </div>
</template>

<script setup>
  const isDark = ref(false)
</script>


<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
}
.container {
  padding: 30px;
}
.dark {
  background: #121212;
  color: white;
  min-height: 100vh;
}

.dark input,
.dark textarea {
  background: #222;
  color: white;
  border: 1px solid #444;
}
</style>


