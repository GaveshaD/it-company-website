<template>
  <section class="contact">
    <h1>Contact Us</h1>

    <p>
      Have a project idea? Let's work together.
    </p>

    <form class="contact-form">
      <input type="text" placeholder="Your Name" required />

      <input type="email" placeholder="Your Email" required />

      <textarea
        placeholder="Your Message"
        rows="6"
        required
    > </textarea>

      <button type="submit">
        Send Message
      </button>
    </form>
  </section>
</template>

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
</style>