<template>
  <section class="projects">
    <h1>Our Projects</h1>
    <p>Here are some projects completed by FutureTech Solutions.</p>

    <div class="filters">
      <button @click="selectedCategory = 'All'">All</button>
      <button @click="selectedCategory = 'Web'">Web</button>
      <button @click="selectedCategory = 'Mobile'">Mobile</button>
    </div>

    <div class="project-grid">
      <ProjectCard
        v-for="project in filteredProjects"
        :key="project.title"
        :title="project.title"
        
      />
 
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue"

const projects = ref([
  {
    title: "Business Website",
    category: "Web"
  },
  {
    title: "E-Commerce Platform",
    category: "Web"
  },
  {
    title: "Mobile App Dashboard",
    category: "Mobile"
  }
])
  const selectedCategory = ref("All")

  const filteredProjects = computed(() => {
  if (selectedCategory.value === "All") {
    return projects.value
  }

  return projects.value.filter(
    project => project.category === selectedCategory.value
  )
})

</script>

<style scoped>
.projects {
  text-align: center;
  padding: 40px 20px;
}

.projects h1 {
  font-size: 42px;
  margin-bottom: 15px;
}

.projects p {
  color: #555;
  margin-bottom: 40px;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

@media (max-width: 800px) {
  .project-grid {
    grid-template-columns: 1fr;
  }
}
.filters {
  margin: 20px 0;
  display: flex;
  justify-content: center;
  gap: 10px;
}

.filters button {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  background: #2563eb;
  color: white;
}

.filters button:hover {
  background: #1d4ed8;
}
</style>