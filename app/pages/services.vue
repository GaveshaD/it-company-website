<template>
  <div>
    <h1 class="title">Our Services</h1>
    <p>We provide a range of IT solutions...</p>

    <p class="service-count">
      We currently offer {{ filteredServices.length }} services.
    </p>

    

    <input
      v-model="searchText"
      class="service-search"
      type="text"
      placeholder="Search by service name or description..."
    />

    <p class="search-hint">
      Search by service title or description.
    </p>

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

      <button
        class="reset-service-filters"
        @click="resetServiceFilters"
      >
        Clear Filters
    </button>

    <button
      :class="{ active: selectedCategory === 'All' }"
      @click="selectedCategory = 'All'"
    >
      All ({{ services.length }})
    </button>

    <button
      :class="{ active: selectedCategory === 'Web' }"
      @click="selectedCategory = 'Web'"
    >
      Web ({{ services.filter(service => service.category === 'Web').length }})
    </button>

    <button
      :class="{ active: selectedCategory === 'Mobile' }"
      @click="selectedCategory = 'Mobile'"
    >
      Mobile ({{ services.filter(service => service.category === 'Mobile').length }})
    </button>

    <button
      :class="{ active: selectedCategory === 'Cloud' }"
      @click="selectedCategory = 'Cloud'"
    >
      Cloud ({{ services.filter(service => service.category === 'Cloud').length }})
    </button>
    </div>

    <p class="selected-service-category">
      Selected category: {{ selectedCategory }}
    </p>


    <div class="services">
      <ServiceCard
        v-for="service in filteredServices"
        :key="service.title"
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

import { services } from "~/data/services"

const searchText = ref("")
const sortOrder = ref("asc")
const selectedCategory = ref("All")


const resetServiceFilters = () => {
  searchText.value = ""
  selectedCategory.value = "All"
  sortOrder.value = "asc"
}

const filteredServices = computed(() => {
  let result =
    selectedCategory.value === "All"
      ? services
      : services.filter(service => service.category === selectedCategory.value)

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
.service-filters button.active {
  background: #2563eb;
  color: white;
}
.reset-service-filters {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  background: #6b7280;
  color: white;
  cursor: pointer;
}
.search-hint {
  text-align: center;
  color: #888;
  font-size: 12px;
  margin-top: -10px;
  margin-bottom: 15px;
}
.selected-service-category {
  text-align: center;
  color: #666;
  font-size: 14px;
  margin-bottom: 20px;
}
.sort-indicator {
  text-align: center;
  color: #666;
  font-size: 14px;
  margin-bottom: 15px;
}
.services {
  animation: fadeIn 0.4s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>