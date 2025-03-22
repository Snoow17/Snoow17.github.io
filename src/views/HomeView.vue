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
  <router-link to="/about" class="link">test</router-link>
</ul>

    </nav>
  </header>

<section class="home" id="home">
  <div class="container">
    <div class="row full-screen">
      <div class="home-content">
        <div class="block">
          <h6>Hello my name is</h6>
          <h1>Jerry Rinzen</h1>
          <h3>Backend/Frontend Student</h3>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="about-me" class="about-me">
  <div class="container">
    <div class="row">
      <div class="section-title">
        <h1>About me</h1>
        <p class="small-text-upper"> Information About Me</p>
      </div>
    </div>
  </div>

<div class="row">
  <div class="about-content">
    <div class="row align-item-center">
      <div class="text">
        <h4>I'm Jerry Rinzen</h4>
        <h6>A <span>Back/Frontend Student</span> based in <span>Sweden</span></h6>
        <p>I'm currently a student learning programing wich is very fun and challenging. So far frontend seems most fun because you get a visual view of what your code can do.</p>

        <p>In addition to learning programming I'm currently working in a hardware store. I would love to be able to make a living out of coding.</p>

        <p>I'm very open to job opportunities where I can contribute, learn and grow.</p>

        <div class="img-me">
          <img src="@/assets/Me.jpg" alt="">
        </div>
      </div>
    </div>
  </div>
</div>

</section>

</template>

<script>
export default {
  name: 'Home'
}
</script>

<style>

.about-content .img-me{
  scale: 75%;
}

.about-me {
    min-height: 100vh;
    background-image: url(https://static.vecteezy.com/system/resources/previews/002/434/224/non_2x/luxury-black-gold-background-elegant-business-presentation-banner-vector.jpg);
    background-size: cover;
    background-position: center;
  }

.about-me .container{
  padding-top: 0.5%;
}

.about-me .section-title .small-text-upper{
  color: var(--text-color);
  padding-top: 0.5%;
}

.about-me .about-content{
  flex: 0 0 100%;
    max-width: 100%;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
}

.about-me .about-content .text p{
  color: var(--text-color);
  font-size: 20px;
  font-weight: 100;
  font-style: italic;
  margin-top: 0.5%;
  padding: 0;
}

.about-me .about-content .text h6{
  color: var(--text-color);
  font-size: 40px;
  font-weight: 400;
  font-style: italic;
  margin: 0;
  padding: 0;
}

.about-me .about-content .text h4{
  color: var(--text-color);
    font-size: 50px;
    font-weight: 400;
    font-style: italic;
    margin: 0;
    padding: 0;
}

  :root {
  --background-color: #060606;
  --text-color: #fff;
  --box-shadow: rgba(255, 255, 255, 0.1);
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

html, body {
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: auto;
  background-color: var(--background-color);
  color: var(--text-color);
}

.container {
  max-width: 1140px;
  margin: 0 auto;
  padding: 0 15px;
}

.row {
  display: flex;
  flex-wrap: wrap;
}

#about {
  scroll-margin-top: 80px;
}

.section-title {
  flex: 0 0 100%;
  max-width: 100%;
  margin-bottom: 40px;
}

.section-title h1 {
  display: inline-block;
  font-size: 35px;
  text-transform: uppercase;
  font-weight: 700;
  color: var(--text-color);
  position: relative;
}

.section-title h1:before {
  content: "";
  left: 0;
  position: absolute;
  height: 2px;
  right: 32%;
  background-color: #febd01;
  bottom: 0;
}

.text-upper {
  text-transform: uppercase;
}

.align-item-center {
  width: 65%;
  align-item: center !important;
  position: relative;
  right: -380px;
}

header {
  position: sticky;
  top: 0;
  width: 100%;
  padding: 20px 5%;
  z-index: 100;
  background-color: var(--background-color);
  box-shadow: 0 4px 8px var(--box-shadow);
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav .nav-logo {
font-size: 30px;
font-weight: 600;
color: var(--text-color);
}

.nav-links .link {
  margin-left: 35px;
}

  .home {
    min-height: 100vh;
    background-image: url(https://wallpapers.com/images/featured-full/notebook-4k-f7k0g3xufpxxwjk9.jpg);
    background-size: cover;
    background-position: center;
  }

  .home .full-screen {
    min-height: 100vh;
  }

  .home .home-content {
    flex: 0 0 100%;
    max-width: 100%;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    margin-left: -250px;
    margin-top: -100px;
  }

  .home .home-content .block {
    flex: 0 0 75%;
    max-width: 75%;
    padding-left: 35px;
    border-left: 5px solid var(--text-color);
    margin-top: 50px;
  }

  .home .home-content .block h6 {
    color: var(--text-color);
    font-size: 40px;
    font-weight: 500;
    margin: 0;
    padding: 0;
  }

  .home .home-content .block h1 {
    color: var(--text-color);
    font-size: 85px;
    font-weight: 700;
    margin: 0;
    padding: 0;
  }

  .home .home-content .block h3 {
    color: var(--text-color);
    font-size: 40px;
    font-weight: 500;
    font-style: italic;
    margin: 0;
    padding: 0;
  }
</style>