<template>
  <div>
    <h1 class="title">Our Services</h1>
    <p>We provide a range of IT solutions...</p>

    <p class="service-count">
      We currently offer {{ services.length }} services.
    </p>

    <p class="featured-count">
      Featured services: {{ featuredCount }}
    </p>

    <p class="category-count">
      Current category count: {{ filteredServices.length }}
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
    <span v-if="searchText">
        for "{{ searchText }}"
      </span>
    </p>

    <p class="service-summary">
      Showing {{ filteredServices.length }} of {{ services.length }} services
    </p>

    <button
      v-if="searchText.trim()"
      class="clear-service-search"
      @click="searchText = ''"
    >
      Clear Search
    </button>

    

    <div class="service-filters">

      <button
        class="reset-service-filters"
        @click="resetServiceFilters"
      >
        Clear Filters
    </button>

    <button
      :class="{ active: showFeaturedOnly }"
      @click="showFeaturedOnly = !showFeaturedOnly"
    >
      Featured Only
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
        :highlighted-title="highlightMatch(service.title)"
        :description="service.description"
        :category="service.category"
        :featured="service.featured"
        @click="selectedService = service"
      />
    </div>

    <div
      v-if="selectedService"
      class="service-modal"
    >
    <h2>{{ selectedService.title }}</h2>

    <p>{{ selectedService.details }}</p>

    <button @click="selectedService = null">
      Close
   </button>
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
const showFeaturedOnly = ref(false)
const selectedService = ref(null)

const resetServiceFilters = () => {
  searchText.value = ""
  selectedCategory.value = "All"
  sortOrder.value = "asc"
  showFeaturedOnly.value = false
}

const highlightMatch = (text) => {
  if (!searchText.value) return text

  const regex = new RegExp(`(${searchText.value})`, "gi")

  return text.replace(regex, "<mark>$1</mark>")
}

const filteredServices = computed(() => {
  let result =
    selectedCategory.value === "All"
      ? services
      : services.filter(service => service.category === selectedCategory.value)

  result = result.filter(service =>
    service.title.toLowerCase().includes(searchText.value.toLowerCase()) ||
    service.description.toLowerCase().includes(searchText.value.toLowerCase()) ||
    service.category.toLowerCase().includes(searchText.value.toLowerCase())
)

  if (showFeaturedOnly.value) {
    result = result.filter(service => service.featured)
}

  return [...result].sort((a, b) =>
    sortOrder.value === "asc"
      ? a.title.localeCompare(b.title)
      : b.title.localeCompare(a.title)
  )
})

const featuredCount = computed(() =>
  services.filter(service => service.featured).length
)
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
.featured-count {
  text-align: center;
  color: #f59e0b;
  font-size: 14px;
  margin-bottom: 15px;
  font-weight: 600;
}
.category-count {
  text-align: center;
  color: #2563eb;
  font-size: 14px;
  margin-bottom: 15px;
  font-weight: 600;
}
.service-modal {
  margin-top: 30px;
  padding: 20px;
  border-radius: 12px;
  background: white;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
</style>