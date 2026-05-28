<template>
  <section class="contact">
    <h1>Contact Us</h1>

    <p>
      Have a project idea? Let's work together.
    </p>
    <p v-if="isSent" class="success-message">
      Your message was sent successfully!
    </p>

    <form class="contact-form"@submit.prevent="sendMessage">
      
      <input type="text" placeholder="Your Name" required />

      <input type="email" placeholder="Your Email" required />

      <textarea
        placeholder="Your Message"
        rows="6"
        required
    > </textarea>
    

<button type="submit" :disabled="isLoading || isSent">
  {{
    isSent
      ? "Message Sent"
      : isLoading
      ? "Sending..."
      : "Send Message"
  }}
</button>
    </form>
  </section>
</template>

<script setup>
const isSent = ref(false)
const isLoading = ref(false)

const sendMessage = () => {
  isLoading.value = true

  setTimeout(() => {
    isLoading.value = false
    isSent.value = true
  }, 2000)
}
</script>

<style scoped>
.contact {
  max-width: 700px;
  margin: auto;
  padding: 40px 20px;
  text-align: center;
}

.contact h1 {
  font-size: 42px;
  margin-bottom: 20px;
}

.contact p {
  color: #555;
  margin-bottom: 40px;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

input,
textarea {
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
}

button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 15px;
  border-radius: 8px;
  font-size: 18px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
.success-message {
  background: #dcfce7;
  color: #166534;
  padding: 15px;
  border-radius: 8px;
  margin-bottom: 20px;
  font-weight: bold;
}
button:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}
</style>