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

<section class="cta">
  <h2>Ready to Build Your Next Project?</h2>

  <p>
    Let's create modern digital solutions together.
  </p>

  <NuxtLink to="/contact" class="cta-button">
    Contact Us
  </NuxtLink>
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
@media (max-width: 600px) {
  .hero h1 {
    font-size: 48px;
  }

  .hero p {
    font-size: 18px;
  }

  .hero {
    padding: 60px 20px;
  }
}
.cta {
  margin-top: 100px;
  text-align: center;
  background: #111827;
  color: white;
  padding: 80px 20px;
  border-radius: 20px;
}

.cta h2 {
  font-size: 42px;
  margin-bottom: 20px;
}

.cta p {
  color: #d1d5db;
  margin-bottom: 30px;
  font-size: 18px;
}

.cta-button {
  display: inline-block;
  background: #2563eb;
  color: white;
  text-decoration: none;
  padding: 14px 28px;
  border-radius: 10px;
  font-weight: bold;
  transition: 0.3s ease;
}

.cta-button:hover {
  background: #1d4ed8;
  transform: translateY(-3px);
}
</style>