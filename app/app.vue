<template>
  <div>
    <nav class="navbar">
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/about">About</NuxtLink>
      <NuxtLink to="/services">Services</NuxtLink>
      <NuxtLink to="/contact">Contact</NuxtLink>
      <NuxtLink to="/projects">Projects</NuxtLink>
      
    </nav>

    <div class="container">
    <NuxtPage />
  </div>
</div>
</template>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
}

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

.container {
  padding: 30px;
}
</style>