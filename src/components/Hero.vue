<template>
  <section class="hero" aria-label="Hero section">
    <div class="hero-content">
      <!-- You can add your main hero headline here if needed -->
    </div>
  </section>
  <div class="hero-bottom-info" aria-label="Movie Library Intro">
    <h1>MOVIE LIBRARY</h1>
    <p>
      Lorem ipsum dolor sit amet, consetetur sadipscing elitr,<br>
      sed diam nonumy eirmod tempor invidunt ut labore et<br>
      dolore magna aliquyam erat, sed diam voluptua.
    </p>
  </div>
</template>

<script>
export default {
  name: 'Hero'
}
</script>

<style>
.hero {
  width: 100vw;
  min-height: 100vh;
  background-image: url('../assets/Images/HeaderImage2.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  padding-top: 96px; /* Adjust to match header/navbar height */
}

.hero::after {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  color: #fff;
  flex: 1 1 auto;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Move .hero-bottom-info outside the image and make it full width */
.hero-bottom-info {
  width: 100vw;
  background: #000000;
  color: #fff;
  text-align: left;
  padding: 2.5rem 2rem 2rem 2rem;
  margin: 0;
  box-sizing: border-box;
}

.hero-bottom-info h1 {
  font-size: 2.2rem;
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 1rem;
}

.hero-bottom-info p {
  font-size: 1.1rem;
  color: #b2c2c2;
  line-height: 1.5;
  margin: 0;
  max-width: 700px;
}

@media (max-width: 700px) {
  .hero-bottom-info {
    padding: 1.2rem 1rem 1rem 1rem;
  }
  .hero-bottom-info h1 {
    font-size: 1.3rem;
  }
  .hero-bottom-info p {
    font-size: 1rem;
  }
}

@media (max-width: 321px) {
  .hero {
    padding-top: 48px;
    min-height: 160vw;

  }
  .hero-bottom-info {
    padding: 0.7rem 0.4rem 0.7rem 0.4rem;
  }
  .hero-bottom-info h1 {
    font-size: 1.5rem;
  }
  .hero-bottom-info p {
    font-size: 0.9rem;
  }
}
</style>