<template>
  <section class="projects">
    <h1>Our Projects</h1>
    <p>Here are some projects completed by FutureTech Solutions.</p>

    <div class="project-grid">
      <div class="project-card">
        <h2>Business Website</h2>
        <p>A responsive company website built for a small business.</p>
      </div>

      <div class="project-card">
        <h2>E-Commerce Platform</h2>
        <p>An online store with product listings and checkout flow.</p>
      </div>

      <div class="project-card">
        <h2>Mobile App Dashboard</h2>
        <p>A clean dashboard UI for managing mobile app users.</p>
      </div>
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

.project-card {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

@media (max-width: 800px) {
  .project-grid {
    grid-template-columns: 1fr;
  }
}
</style>