<template>
  <nav class="navbar">
    <NuxtLink to="/">Home</NuxtLink>
    <NuxtLink to="/about">About</NuxtLink>
    <NuxtLink to="/services">Services</NuxtLink>
    <NuxtLink to="/projects">Projects</NuxtLink>
    <NuxtLink to="/contact">Contact</NuxtLink>
  </nav>
</template>

<style scoped>
.navbar {
  background-color: #222;
  padding: 20px;
  display: flex;
  gap: 20px;
}

.navbar a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

.router-link-exact-active {
  color: #00aaff !important;
  border-bottom: 2px solid #00aaff;
  padding-bottom: 5px;
}
</style>