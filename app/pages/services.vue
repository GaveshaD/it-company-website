<template>
  <div>
    <h1 class="title">Our Services</h1>

    <div class="services">
      <ServiceCard
        title="Web Development"
        description="Modern responsive websites using Nuxt and Vue."
      />

      <ServiceCard
        title="Mobile Apps"
        description="Android and iOS application development."
      />

      <ServiceCard
        title="Cloud Solutions"
        description="Scalable cloud infrastructure and deployment."
      />

      
    </div>
  </div>
</template>

<style scoped>
.title {
  text-align: center;
  margin-bottom: 40px;
}

.services {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

/* Tablet */
@media (max-width: 900px) {
  .services {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Mobile */
@media (max-width: 600px) {
  .services {
    grid-template-columns: 1fr;
  }
}
</style>