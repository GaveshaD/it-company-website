<template>
  <section class="projects">
    <h1>Our Projects</h1>
    <p>Here are some projects completed by FutureTech Solutions.</p>

    <div class="project-grid">
      <ProjectCard
        title="Business Website"
        description="A responsive company website built for a small business."
      />

      <ProjectCard
        title="E-Commerce Platform"
        description="An online store with product listings and checkout flow."
      />

      <ProjectCard
        title="Mobile App Dashboard"
        description="A clean dashboard UI for managing mobile app users."
      />

      
    </div>
  </section>
</template>

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
</style>