<template>
  <section class="contact-map">
    <form class="contact-form" @submit.prevent="onSubmit">
      <h2>Contact Us</h2>
      <div class="form-group">
        <input v-model="firstName" placeholder="First Name*" :class="{ error: errors.firstName }" />
        <div v-if="errors.firstName" class="error-msg">First name is required.</div>
      </div>
      <div class="form-group">
        <input v-model="lastName" placeholder="Last Name*" :class="{ error: errors.lastName }" />
        <div v-if="errors.lastName" class="error-msg">Last name is required.</div>
      </div>
      <div class="form-group">
        <input v-model="email" placeholder="Email*" :class="{ error: errors.email }" />
        <div v-if="errors.email" class="error-msg">Valid email is required.</div>
      </div>
      <div class="form-group">
        <textarea v-model="message" placeholder="Message*" :class="{ error: errors.message }"></textarea>
        <div v-if="errors.message" class="error-msg">Message is required.</div>
      </div>
      <button type="submit">Send</button>
    </form>
    <div class="map-embed">
      <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3036.370073262316!2d-3.627499684606019!3d40.46524697936009!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422e6b1b1e2e7b%3A0x7e2e2e2e2e2e2e2e!2sAmadeus%20IT%20Group%2C%20S.A.!5e0!3m2!1sen!2ses!4v1620000000000!5m2!1sen!2ses" width="100%" height="300" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactMap',
  data() {
    return {
      firstName: '',
      lastName: '',
      email: '',
      message: '',
      errors: {}
    }
  },
  methods: {
    onSubmit() {
      this.errors = {};
      if (!this.firstName) this.errors.firstName = true;
      if (!this.lastName) this.errors.lastName = true;
      if (!this.email || !/^[^@\s]+@[^@\s]+\.[^@\s]+$/.test(this.email)) this.errors.email = true;
      if (!this.message) this.errors.message = true;
      if (Object.keys(this.errors).length === 0) {
        alert(`First Name: ${this.firstName}\nLast Name: ${this.lastName}\nEmail: ${this.email}\nMessage: ${this.message}`);
        this.firstName = this.lastName = this.email = this.message = '';
      }
    }
  }
}
</script>

<style scoped>
.contact-map { display: flex; flex-wrap: wrap; gap: 2rem; justify-content: center; align-items: flex-start; padding: 2rem 1rem; }
.contact-form { background: #fff; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.07); padding: 2rem; width: 340px; }
.contact-form h2 { margin-bottom: 1rem; }
.form-group { margin-bottom: 1rem; }
input, textarea { width: 100%; padding: 0.5rem; border: 1px solid #ccc; border-radius: 4px; font-size: 1rem; }
input.error, textarea.error { border-color: #e74c3c; }
.error-msg { color: #e74c3c; font-size: 0.95rem; margin-top: 0.2rem; }
button { background: #0078d7; color: #fff; border: none; border-radius: 4px; padding: 0.7rem 1.5rem; font-size: 1rem; cursor: pointer; transition: background 0.2s; }
button:hover { background: #005fa3; }
.map-embed { flex: 1 1 320px; min-width: 320px; max-width: 600px; }
@media (max-width: 900px) {
  .contact-map { flex-direction: column; align-items: stretch; }
  .map-embed { margin-top: 2rem; }
}
</style>
