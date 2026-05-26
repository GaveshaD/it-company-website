<template>
  <section class="hero">
    <h1>FutureTech Solutions</h1>

    <p>
      We build modern websites, mobile applications, and cloud solutions
      for businesses.
    </p>

    <button>Get Started</button>
  </section>

  <section class="testimonials">
  <SectionTitle
    title="What Our Clients Say"
    subtitle="Trusted by businesses around the world."
  />

  <div class="testimonial-grid">
    <TestimonialCard
      message="FutureTech built an amazing website for our company."
      name="John Doe"
      role="Business Owner"
    />

    <TestimonialCard
      message="Professional team and excellent support."
      name="Sarah Smith"
      role="Startup Founder"
    />

    <TestimonialCard
      message="Their cloud solutions improved our infrastructure."
      name="Michael Lee"
      role="Tech Lead"
    />
  </div>
</section>

</template>



<style scoped>
.hero {
  text-align: center;
  padding: 120px 20px;
  background: linear-gradient(135deg, #0f172a, #1e3a8a);
  color: white;
  border-radius: 20px;
  margin-top: 30px;
}
.hero h1 {
  font-size: 56px;
  margin-bottom: 20px;
  color: white;
}
.hero p {
  font-size: 20px;
  max-width: 700px;
  margin: auto;
  color: #e2e8f0;
  line-height: 1.6;
}

button {
  margin-top: 30px;
  padding: 14px 30px;
  border: none;
  background-color: #007bff;
  color: white;
  font-size: 18px;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.testimonials {
  margin-top: 100px;
}

.testimonial-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

@media (max-width: 900px) {
  .testimonial-grid {
    grid-template-columns: 1fr;
  }
}
</style>