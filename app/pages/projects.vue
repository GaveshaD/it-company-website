<template>
  <section class="projects">
    <h1>Our Projects</h1>
    <p>Here are some projects completed by FutureTech Solutions.</p>

    <div class="filters">
      <button
        :class="{ active: selectedCategory === 'All' }"
        @click="selectedCategory = 'All'"
    >
        All ({{ projects.length }})
      </button>

      <button
        :class="{ active: selectedCategory === 'Web' }"
        @click="selectedCategory = 'Web'"
    >
        Web ({{ projects.filter(project => project.category === 'Web').length }})
      </button>

      <button
        :class="{ active: selectedCategory === 'Mobile' }"
        @click="selectedCategory = 'Mobile'"
    >
        Mobile ({{ projects.filter(project => project.category === 'Mobile').length }})
      </button>

      <button
        :class="{ active: selectedCategory === 'Cloud' }"
        @click="selectedCategory = 'Cloud'"
    >
        Cloud ({{ projects.filter(project => project.category === 'Cloud').length }})
</button>
    </div>

    <div class="project-grid">
      <ProjectCard
        v-for="project in filteredProjects"
        :key="project.title"
        :title="project.title"
        :description="project.description"
        
      />
      <p v-if="filteredProjects.length === 0" class="no-projects">
        No projects found.
      </p>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue"

import { projects } from "~/data/projects"

const selectedCategory = ref("All")

const filteredProjects = computed(() => {
  if (selectedCategory.value === "All") {
    return projects
  }

  return projects.filter(
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
.filters {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin: 20px 0;
}

.filters button {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  background: #e5e7eb;
}

.filters button.active {
  background: #2563eb;
  color: white;
}
.no-projects {
  text-align: center;
  color: #666;
  margin-top: 30px;
}
</style>