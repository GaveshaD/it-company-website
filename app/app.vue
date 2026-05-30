<template>
  <div :class="{ dark: isDark }">
    <Navbar />

    <button class="theme-toggle" @click="isDark = !isDark">
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

onMounted(() => {
  const savedTheme = localStorage.getItem("darkMode")

  if (savedTheme !== null) {
    isDark.value = savedTheme === "true"
  }
})

watch(isDark, (newValue) => {
  localStorage.setItem("darkMode", newValue)
})
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
.theme-toggle {
  margin: 20px 30px 0;
  padding: 10px 18px;
  border: none;
  border-radius: 999px;
  background: #2563eb;
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s ease;
}

.theme-toggle:hover {
  background: #1d4ed8;
  transform: translateY(-2px);
}
</style>


