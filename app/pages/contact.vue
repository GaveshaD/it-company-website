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
        
      />

      <input
        type="email"
        placeholder="Your Email"
        v-model="email"
        
      />
      <p v-if="email && !email.includes('@')" class="error-text">
        Invalid email format
      </p>

      <textarea
        placeholder="Your Message"
        rows="6"
        v-model="message"
        maxlength="200"
        
      ></textarea>

      <p
        class="char-count"
        :class="{ warning: 200 - message.length < 20 }"
      >
        {{ 200 - message.length }} characters remaining
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

<button
  type="button"
  class="reset-btn"
  @click="resetForm"
>
  Clear Form
</button>

      <p v-if="submitCount > 0" class="submit-count">
          Messages sent: {{ submitCount }}
      </p>


      <p v-if="lastSubmitted" class="last-submitted">
          Last submitted at: {{ lastSubmitted }}
      </p>

    </form>
  </section>
</template>

<script setup>
const isSent = ref(false)
const isLoading = ref(false)
const submitCount = ref(0)
const lastSubmitted = ref("")

const name = ref("")
const email = ref("")
const message = ref("")
const errorMessage = ref("")

const sendMessage = () => {
  errorMessage.value = ""
  isSent.value = false

  if (!name.value || !email.value || !message.value) {
    errorMessage.value = "Please fill all fields."
    return
  }

  if (!email.value.includes("@")) {
    errorMessage.value = "Please enter a valid email."
    return
  }

  isLoading.value = true

setTimeout(() => {
  isLoading.value = false
  isSent.value = true

  submitCount.value++

  lastSubmitted.value = new Date().toLocaleTimeString()

  name.value = ""
  email.value = ""
  message.value = ""

  setTimeout(() => {
    isSent.value = false
  }, 3000)

}, 2000)
}

const resetForm = () => {
  name.value = ""
  email.value = ""
  message.value = ""

  isSent.value = false
  errorMessage.value = ""
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
.reset-btn {
  width: 100%;
  margin-top: 10px;
  padding: 14px;
  border: none;
  border-radius: 8px;
  background: #6b7280;
  color: white;
  cursor: pointer;
}

.reset-btn:hover {
  background: #4b5563;
}
.error-text {
  color: red;
  font-size: 14px;
  margin-top: 5px;
  margin-bottom: 10px;
}
input:focus,
textarea:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.2);
}
.submit-count {
  text-align: center;
  margin-top: 15px;
  color: #666;
  font-size: 14px;
}
.warning {
  color: red;
  font-weight: bold;
}
.last-submitted {
  text-align: center;
  color: #666;
  font-size: 14px;
}
</style>