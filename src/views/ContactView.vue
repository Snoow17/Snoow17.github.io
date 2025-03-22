<template>
    <header>
    <nav>
      <div class="nav-logo">
        <h1>Portfolio.</h1>
      </div>

<ul class="nav-links">
  <router-link to="/" class="link">Home</router-link>
  <router-link to="/projects" class="link">Projects</router-link>
  <router-link to="/contact" class="link">Contact</router-link>
</ul>
    </nav>
    </header>

<div class="email-form">
  <form ref="form" @submit.prevent="sendEmail">
    <label>Name</label>
    <input type="text" name="user_name" required>
    <label>Email</label>
    <input type="email" name="user_email" required>
    <label>Message</label>
    <textarea name="message" required></textarea>
    <button class="submit-btn" type="submit">{{ buttonText }}</button>
  </form>
</div>
  </template>

<script>
import emailjs from '@emailjs/browser';


export default {
  data() {
    return {
      buttonText: 'Send',
    };
  },
  methods: {
    sendEmail() {

this.buttonText = 'Message has been sent!';

      emailjs
        .sendForm('j.rinzen@live.se', 'template_kfjqizo', this.$refs.form, {
          publicKey: 'jpwILXbcI8hkDusag',
        })
        .then(
          () => {
            console.log('SUCCESS!');

            this.$refs.form.reset();
            setTimeout(() => {
              this.buttonText = 'Send';
            }, 5000);
          },
          (error) => {
            console.log('FAILED...', error.text);

            this.buttonText = 'Send';
          },
        );
    },
  },
};
</script>

<style scoped>

.email-form {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  background-color: #f9f9f9;
}

.email-form input, .email-form textarea {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  padding: 10px;
  margin: 20px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.email-form button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.email-form button:hover {
  background-color: #0056b3;
}


</style>