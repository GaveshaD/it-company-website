<template>
  <div class="testimonial-card">
    <p class="message">
      "{{ message }}"
    </p>

    <h3>{{ name }}</h3>

    <span>{{ role }}</span>
  </div>
</template>

<script setup>
defineProps({
  message: String,
  name: String,
  role: String
})
</script>

<style scoped>
.testimonial-card {
  background: white;
  padding: 30px;
  border-radius: 16px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  transition: 0.3s ease;
}

.testimonial-card:hover {
  transform: translateY(-10px);
}

.message {
  font-size: 18px;
  color: #444;
  line-height: 1.6;
  margin-bottom: 20px;
}

h3 {
  margin-bottom: 5px;
}

span {
  color: #777;
}
</style>