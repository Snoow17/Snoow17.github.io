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

  <section class="projects" id="projects">
    <div class="container">
      <div class="row full-screen">
        <div class="project-content">
          <div 
            v-for="(image, index) in images" 
            :key="index" 
            class="image-container"
            @click="showInfo(index)"
          >
            <img 
              :src="image.src" 
              :alt="image.alt" 
            />
          </div>
        </div>
      </div>
    </div>

    <!-- Modal for Larger Image and Additional Pictures -->
    <div v-if="isModalVisible" class="modal-overlay" @click="closeModal">
      <div class="modal" @click.stop>
        <div class="modal-main-image">
          <img :src="selectedImage.src" :alt="selectedImage.alt" class="modal-image" />
          <h2>{{ selectedImage.alt }}</h2>
          <p>{{ selectedImage.info }}</p>
        </div>

        <!-- Additional Images -->
        <div class="modal-additional-images">
          <h3>More Images</h3>
          <div class="additional-images">
            <div
              v-for="(image, index) in selectedImage.additionalImages"
              :key="index"
              class="additional-image-container"
              :class="{'active': enlargedImageIndex === index}"
              @click="enlargeImage(index)"
            >
              <img :src="image.src" :alt="image.alt" class="additional-image" />
            </div>
          </div>
        </div>

        <button @click="closeModal">Close</button>
      </div>
    </div>

    
    <div v-if="enlargedImageIndex !== null" class="enlarged-image-overlay" @click="closeEnlargedImage">
      <div class="enlarged-image-container" @click.stop>
        <img 
          :src="selectedImage.additionalImages[enlargedImageIndex].src" 
          :alt="selectedImage.additionalImages[enlargedImageIndex].alt" 
          class="enlarged-image" 
        />
        <button class="close-enlarged-btn" @click="closeEnlargedImage">Close</button>
      </div>
    </div>
  </section>
</template>


<script>
export default {
  data() {
    return {
      selectedIndex: null,  
      isModalVisible: false,  
      selectedImage: {},  
      enlargedImageIndex: null,  
      images: [
        {
          src: require('@/assets/SQL/SQLlogo.jpg'), 
          alt: 'Logo 1', 
          info: 'I learned how to create SQL Databases and we made a library application with it that tracks books, borrowers and loans.',
          additionalImages: [
            { src: require('@/assets/SQL/Books.png'), alt: 'Logo 1 - A' },
            { src: require('@/assets/SQL/BooksDiagram.png'), alt: 'Logo 1 - B' },
            { src: require('@/assets/SQL/Borrowers.png'), alt: 'Logo 1 - C' },
            { src: require('@/assets/SQL/Loans.png'), alt: 'Logo 1 - D' }
          ]
        },
        {
          src: require('@/assets/logo.png'), 
          alt: 'Logo 2', 
          info: 'My first Vue project during studies were we made a Calculator, a Clock, a Counter, a Dice and some FAQ. Buttons are pressable and FAQ can show/hide answers.',
          additionalImages: [
            { src: require('@/assets/FirstVue/CalcView.png'), alt: 'Logo 2 - A' },
            { src: require('@/assets/FirstVue/CalcVue.png'), alt: 'Logo 2 - B' },
            { src: require('@/assets/FirstVue/ClockView.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/ClockVue.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/CounterComponent.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/CountersView.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/CountersVue.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/DiceView.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/DiceVue.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/FAQView.png'), alt: 'Logo 2 - C' },
            { src: require('@/assets/FirstVue/FAQVue.png'), alt: 'Logo 2 - C' }
          ]
        },
        {
          src: require('@/assets/Fizzbuzz/Logo.jpg'), 
          alt: 'Logo 3', 
          info: 'Fizzbuzz project. Prints fizz, buzz or fizzbuzz in console if numbers are devided with the right property.',
          additionalImages: [
            { src: require('@/assets/Fizzbuzz/FizzbuzzCode.png'), alt: 'Logo 3 - A' },
            { src: require('@/assets/Fizzbuzz/FizzbuzzView.png'), alt: 'Logo 3 - B' }
          ]
        },
        {
          src: require('@/assets/TicTacToe/Logo.png'), 
          alt: 'Logo 4', 
          info: 'Tictactoe in console window.',
          additionalImages: [
            { src: require('@/assets/TicTacToe/Code1.png'), alt: 'Logo 4 - A' },
            { src: require('@/assets/TicTacToe/Code2.png'), alt: 'Logo 4 - B' },
            { src: require('@/assets/TicTacToe/Game.png'), alt: 'Logo 4 - c' }
          ]
        },
        // Add more images here
      ]
    };
  },
  methods: {
    showInfo(index) {
      this.selectedIndex = index;  
      this.selectedImage = this.images[index];  
      this.isModalVisible = true;  
    },
    closeModal() {
      this.isModalVisible = false;  
      this.enlargedImageIndex = null;  
    },
    enlargeImage(index) {
      this.enlargedImageIndex = index;  
    },
    closeEnlargedImage() {
      this.enlargedImageIndex = null;  
    }
  }
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

.project-content {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 100px;
}

.image-container {
  display: inline-block;
  margin: 10px;
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
}

.image-container img {
  width: 200px;
  height: auto;
  transition: transform 0.3s ease-in-out;
}

.image-container.selected img {
  transform: scale(1.2);
  z-index: 10;
}


.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
}

.modal {
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
}

.modal-main-image {
  margin-bottom: 20px;
}

.modal-image {
  width: 100%;
  height: auto;
  max-width: 600px; 
  margin-bottom: 20px;
}

button {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
}

button:hover {
  background-color: #0056b3;
}


.modal-additional-images {
  margin-top: 20px;
}

.additional-images {
  display: flex;
  gap: 20px;
  justify-content: center;
  flex-wrap: wrap;
}

.additional-image-container {
  position: relative;
  cursor: pointer;
  transition: transform 0.3s ease-in-out;
}

.additional-image {
  width: 100px;
  height: auto;
  transition: transform 0.3s ease-in-out; 
}

.additional-image:hover {
  transform: scale(1.1); 
}


.additional-image-container.active .additional-image {
  transform: scale(5); 
  transition: transform 0.5s ease-in-out;
}


.additional-image-container.active {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: 200; 
  display: flex;
  justify-content: center;
  align-items: center;
}

.enlarged-image-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 300;
}

.enlarged-image-container {
  position: relative;
  max-width: 90vw;
  max-height: 90vh;
  overflow: hidden;
}

.enlarged-image {
  width: 100%;
  height: auto;
  transition: transform 0.3s ease-in-out;
}

.close-enlarged-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #ff4d4d;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  font-size: 1.5rem;
}

.close-enlarged-btn:hover {
  background-color: #ff1a1a;
}
</style>
