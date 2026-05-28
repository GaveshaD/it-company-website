<template>
  <section class="contact">
    <h1>Contact Us</h1>

    <p>
      Have a project idea? Let's work together.
    </p>
    <p v-if="isSent" class="success-message">
      Your message was sent successfully!
    </p>

    <p v-if="errorMessage" class="error-message">
      {{ errorMessage }}
    </p>

    <form class="contact-form"@submit.prevent="sendMessage">
      
      <input
        type="text"
        placeholder="Your Name"
        v-model="name"
        required
      />

      <input
        type="email"
        placeholder="Your Email"
        v-model="email"
        required
      />

      <textarea
        placeholder="Your Message"
        rows="6"
        v-model="message"
        maxlength="200"
        required
      ></textarea>

      <p class="char-count">
          {{ message.length }}/200 characters
      </p>
    

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

const name = ref("")
const email = ref("")
const message = ref("")
const errorMessage = ref("")

const sendMessage = () => {
  errorMessage.value = ""
  isLoading.value = true

  setTimeout(() => {
    isLoading.value = false
    isSent.value = true

    name.value = ""
    email.value = ""
    message.value = ""
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
.char-count {
  text-align: right;
  margin-top: 8px;
  color: #666;
  font-size: 14px;
}
.error-message {
  background: #fee2e2;
  color: #991b1b;
  padding: 15px;
  border-radius: 8px;
  margin-bottom: 20px;
  font-weight: bold;
}
</style>