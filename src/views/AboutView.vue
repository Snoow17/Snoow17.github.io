<template>
  <form ref="form" @submit.prevent="sendEmail">
    <label>Name</label>
  <input type="text" name="user_name" required />
  
  <label>Email</label>
  <input type="email" name="user_email" required />
  
  <label>Message</label>
  <textarea name="message" required></textarea>
    <input type="submit" value="Send">
  </form>
</template>

<script>
import emailjs from '@emailjs/browser';

export default {
  methods: {
    sendEmail() {
      emailjs
        .sendForm('service_w1clzgj', 'contact_form', this.$refs.form, {
          publicKey: 'jpwILXbcI8hkDusag',
        })
        .then(
          () => {
            console.log('SUCCESS!');
          },
          (error) => {
            console.log('FAILED...', error.text);
          },
        );
    },
  },
};
</script>