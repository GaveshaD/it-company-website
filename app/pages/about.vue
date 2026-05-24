<template>
  <section class="about">
    <h1>About FutureTech Solutions</h1>

    <p>
      FutureTech Solutions is a modern IT company focused on building
      high-quality digital products for businesses.
    </p>

    <p>
      We specialize in web development, mobile applications,
      cloud infrastructure, and modern user experiences.
    </p>

    <div class="stats">
      <div class="stat-card">
        <h2>10+</h2>
        <p>Projects Completed</p>
      </div>

      <div class="stat-card">
        <h2>5+</h2>
        <p>Team Members</p>
      </div>

      <div class="stat-card">
        <h2>24/7</h2>
        <p>Support</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  max-width: 1000px;
  margin: auto;
  padding: 40px 20px;
  text-align: center;
}

.about h1 {
  font-size: 42px;
  margin-bottom: 20px;
}

.about p {
  font-size: 18px;
  line-height: 1.7;
  color: #555;
  margin-bottom: 20px;
}

.stats {
  margin-top: 50px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.stat-card {
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

.stat-card h2 {
  font-size: 36px;
  color: #007bff;
}

@media (max-width: 700px) {
  .stats {
    grid-template-columns: 1fr;
  }
}
</style>