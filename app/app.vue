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
  <button
    v-if="showTopButton"
    class="back-to-top"
    @click="scrollToTop"
  >
  ⬆️
  </button>
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

const showTopButton = ref(false)

const handleScroll = () => {
  showTopButton.value = window.scrollY > 300
}

onMounted(() => {
  window.addEventListener("scroll", handleScroll)
})

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll)
})

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: "smooth"
  })
}
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
body,
.container,
.dark,
input,
textarea,
button {
  transition:
    background-color 0.3s ease,
    color 0.3s ease,
    border-color 0.3s ease;
}
.dark .theme-toggle {
  background: #130b31;
}

.dark .theme-toggle:hover {
  background: #130b31;
}

.back-to-top {
  position: fixed;
  bottom: 20px;
  right: 20px;

  width: 50px;
  height: 50px;

  border: none;
  border-radius: 50%;

  background: #2563eb;
  color: white;

  font-size: 20px;
  cursor: pointer;

  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}

.back-to-top:hover {
  background: #1d4ed8;
}
</style>


