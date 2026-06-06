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

    <select v-model="sortOrder" class="service-sort">
      <option value="asc">A → Z</option>
      <option value="desc">Z → A</option>
    </select>

    <p class="service-results">
      {{ filteredServices.length }} service(s) found
    </p>

    <p class="service-summary">
      Showing {{ filteredServices.length }} of {{ services.length }} services
    </p>

    <button
      v-if="searchText"
      class="clear-service-search"
      @click="searchText = ''"
    >
      Clear
    </button>

    <div class="service-filters">
      <button @click="selectedCategory = 'All'">All</button>
      <button @click="selectedCategory = 'Web'">Web</button>
      <button @click="selectedCategory = 'Mobile'">Mobile</button>
      <button @click="selectedCategory = 'Cloud'">Cloud</button>
    </div>

    <div class="services">
      <ServiceCard
        v-for="service in filteredServices"
        :key="service.title"
        :icon="service.icon"
        :title="service.title"
        :description="service.description"
        :category="service.category"
      />
    </div>

    <p v-if="filteredServices.length === 0" class="no-services">
      No services found.
    </p>
  </div>
</template>

<script setup>
import { ref, computed } from "vue"

const searchText = ref("")
const sortOrder = ref("asc")
const selectedCategory = ref("All")

const services = [
  {
    
    title: "Web Development",
    description: "Modern responsive websites using Nuxt and Vue.",
    category: "Web"
  },
  {
    
    title: "Mobile Apps",
    description: "Android and iOS application development.",
    category: "Mobile"
  },
  {
    
    title: "Cloud Solutions",
    description: "Scalable cloud infrastructure and deployment.",
    category: "Cloud"
  }
]

const filteredServices = computed(() => {
  let result =
    selectedCategory.value === "All"
      ? services
      : services.filter(
          service => service.category === selectedCategory.value
        )

  result = result.filter(service =>
    service.title.toLowerCase().includes(searchText.value.toLowerCase()) ||
    service.description.toLowerCase().includes(searchText.value.toLowerCase())
  )

  return [...result].sort((a, b) =>
    sortOrder.value === "asc"
      ? a.title.localeCompare(b.title)
      : b.title.localeCompare(a.title)
  )
})
</script>

<style scoped>
.title {
  text-align: center;
  margin-bottom: 40px;
}

.service-count,
.service-results,
.service-summary {
  text-align: center;
  color: #666;
  margin-bottom: 20px;
  font-size: 14px;
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

.service-sort {
  display: block;
  margin: 10px auto 20px;
  padding: 8px;
  border-radius: 6px;
}

.clear-service-search {
  display: block;
  margin: 0 auto 20px;
  padding: 8px 16px;
  border: none;
  border-radius: 8px;
  background: #ef4444;
  color: white;
  cursor: pointer;
}

.clear-service-search:hover {
  opacity: 0.9;
}

.service-filters {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin: 20px 0;
}

.service-filters button {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.services {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.no-services {
  text-align: center;
  color: #666;
  margin-top: 20px;
}

@media (max-width: 900px) {
  .services {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .services {
    grid-template-columns: 1fr;
  }
}
</style>