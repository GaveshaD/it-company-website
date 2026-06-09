<template>
  <div class="card" :class="category.toLowerCase()">

    <span v-if="featured" class="featured-badge">
      ⭐ Featured
    </span>
    

    <h2 v-html="highlightedTitle || title"></h2>

    <p>{{ description }}</p>

    <span
      class="service-category"
      :class="category.toLowerCase()"
    >
      {{ category }}
    </span>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  category: String,
  highlightedTitle: String,
  featured: Boolean
})
</script>

<style scoped>
.card {
  background: white;
  padding: 25px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

.card h2 {
  margin-bottom: 10px;
  color: #222;
}

.card p {
  color: #555;
  line-height: 1.5;
}



.service-category {
  display: inline-block;
  margin-top: 10px;
  padding: 4px 10px;
  border-radius: 999px;
  color: white;
  font-size: 12px;
}

.service-category.web {
  background: #2563eb;
}

.service-category.mobile {
  background: #16a34a;
}

.service-category.cloud {
  background: #9333ea;
}
mark {
  background: #facc15;
  padding: 2px 4px;
  border-radius: 4px;
}
.featured-badge {
  display: inline-block;
  background: gold;
  color: #333;
  padding: 4px 10px;
  border-radius: 999px;
  font-size: 12px;
  font-weight: bold;
  margin-bottom: 10px;
}
.card.web {
  border-left: 4px solid #2563eb;
}

.card.mobile {
  border-left: 4px solid #16a34a;
}

.card.cloud {
  border-left: 4px solid #9333ea;
}
</style>