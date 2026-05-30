<template>
  <button
    v-if="showTopButton"
    class="back-to-top"
    @click="scrollToTop"
  >
    ⬆️
  </button>
</template>

<script setup>
const showTopButton = ref(false)

const handleScroll = () => {
  showTopButton.value = window.scrollY > 10
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

<style scoped>
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