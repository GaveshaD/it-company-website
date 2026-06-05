<template>
  <div>
    <h1 class="title">Our Services</h1>
    <p>We provide a range of IT solutions...</p>

    <p class="service-count">
      We currently offer {{ services.length }} services.
    </p>

    <input
      v-model="searchText"
      class="service-search"
      type="text"
      placeholder="Search services..."
    />

    <div class="services">
      <ServiceCard
        v-for="service in filteredServices"
        :key="service.title"
        :icon="service.icon"
        :title="service.title"
        :description="service.description"
      />

      <p v-if="filteredServices.length === 0" class="no-services">
        No services found.
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue"

const searchText = ref("")

const services = [
  {
    icon: "🌐",
    title: "Web Development",
    description: "Modern responsive websites using Nuxt and Vue."
  },
  {
    icon: "📱",
    title: "Mobile Apps",
    description: "Android and iOS application development."
  },
  {
    icon: "☁️",
    title: "Cloud Solutions",
    description: "Scalable cloud infrastructure and deployment."
  }
]

const filteredServices = computed(() =>
  services.filter(service =>
    service.title.toLowerCase().includes(searchText.value.toLowerCase()) ||
    service.description.toLowerCase().includes(searchText.value.toLowerCase())
  )
)
</script>

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
.service-count {
  text-align: center;
  color: #666;
  margin-bottom: 20px;
}
.service-search {
  width: 100%;
  max-width: 500px;
  padding: 12px;
  margin: 20px auto;
  display: block;
  border: 1px solid #ccc;
  border-radius: 8px;
}
.no-services {
  text-align: center;
  color: #666;
  margin-top: 20px;
}
</style>