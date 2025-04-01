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

  <section class="contact" id="contact">
  <div class="container">
    <div class="row full-screen">
      <div class="contact-content">
        <div class="block">
          <div class="container">
          <h1>Contact me!</h1>
          <p class="subtext">Best way to reach me is through Email, but if other sources are better for you, feel free to contact me there.</p>

          <div class="icons">

          <div class="icon" @click="openModal('email')">
          <i class="fas fa-envelope fa-4x email-icon"></i> 
          </div>

        
          <div class="icon" @click="openModal('facebook')">
          <i class="fab fa-facebook fa-4x facebook-icon"></i> 
         </div>

        
        <div class="icon" @click="openModal('x')">
          <i class="fab fa-twitter fa-4x twitter-icon"></i> 
        </div>

        
        <div class="icon" @click="openModal('instagram')">
          <i class="fab fa-instagram fa-4x instagram-icon"></i> 
        </div>

        
        <div class="icon" @click="openModal('github')">
          <i class="fab fa-github fa-4x github-icon"></i> 
        </div>
      </div>

      
      <div v-if="modalOpen" class="modal-overlay" @click.self="closeModal">
        <div class="modal-content">
          <button class="close-btn" @click="closeModal">X</button>
          <h2>Contact via {{ activeIcon }}</h2>
          <p v-if="activeIcon === 'email'">Email: <a href="mailto:j.rinzen@live.se">j.rinzen@live.se</a></p>
          <p v-if="activeIcon === 'facebook'">Facebook: <a href="https://www.facebook.com/" target="_blank">Myprofile</a></p>
          <p v-if="activeIcon === 'x'">Twitter: <a href="https://twitter.com/" target="_blank">@Myprofile</a></p>
          <p v-if="activeIcon === 'instagram'">Instagram: <a href="https://www.instagram.com/" target="_blank">Myprofile</a></p>
          <p v-if="activeIcon === 'github'">GitHub: <a href="https://github.com/snoow17" target="_blank">Snoow17</a></p>
        </div>
      </div>
    </div>
        </div>
      </div>
    </div>
  </div>
</section>
</template>

<script>
export default {
  data() {
    return {
      activeIcon: null,
      modalOpen: false,
    };
  },
  methods: {
    openModal(icon) {
      this.activeIcon = icon;
      this.modalOpen = true;
    },
    closeModal() {
      this.modalOpen = false;
      this.activeIcon = null;
    },
  },
};
</script>

<style scoped>
header {
  position: sticky;
  top: 0;
  width: 100%;
  padding: 20px 5%;
  z-index: 100;
  background-color: var(--background-color);
  box-shadow: 0 4px 8px var(--box-shadow);
}

.contact .contact-content .block h1 {
  color: var(--text-color);
    font-size: 85px;
    font-weight: 700;
    margin: 0;
    padding: 15px;
}

.subtext {
  font-size: 1.2rem;
  color: white;
  margin-bottom: 30px;
}

.icons {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.icon {
  display: inline-block;
  cursor: pointer;
  transition: transform 0.2s;
}

.icon:hover {
  transform: scale(1.1);
}

.icon-info {
  text-align: center;
  margin-top: 10px;
}

.icon-info i {
  margin-bottom: 5px;
}

.icon-info p {
  font-size: 1rem;
}

.icon-info a {
  color: #0073e6;
  text-decoration: none;
}

.icon-info a:hover {
  text-decoration: underline;
}


.email-icon {
  color: #0073e6; 
}

.facebook-icon {
  color: #3b5998; 
}

.twitter-icon {
  color: #1DA1F2; 
}

.instagram-icon {
  color: #E4405F; 
}

.github-icon {
  color: #333; 
}


.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  max-width: 500px;
  width: 100%;
}

.close-btn {
  background-color: #ff4b5c;
  color: white;
  border: none;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  margin-bottom: 20px;
}

.close-btn:hover {
  background-color: #ff2a34;
}
</style>
