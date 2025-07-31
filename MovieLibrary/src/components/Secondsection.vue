<template>
  <section class="movie-library">
    
    <div class="library-favourites">
      <h2>Collect your favourites</h2>
      <form class="search-form">
        <input type="text" placeholder="Search title and add to grid" />
      </form>
    </div>
    <hr />
    <div class="movie-grid">
      <!-- Batman Card -->
      <div class="movie-card">
        <img src="../assets/Images/Batman.jpg" alt="Batman" />
        <button class="close-btn">×</button>
        <div class="movie-info">
          <h3>Batman Returns</h3>
          <p>Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…</p>
        </div>
      </div>
      <!-- Wild West Card -->
      <div class="movie-card">
        <img src="../assets/Images/Wild West.jpg" alt="Wild West" />
        <button class="close-btn">×</button>
        <div class="movie-info">
          <h3>Wild Wild Wes t</h3>
          <p>Lorem ipsum dolor sit a met, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut…</p>
        </div>
      </div>
      <!-- Spiderman Card -->
      <div class="movie-card">
        <img src="../assets/Images/Spiderman.jpg" alt="Spiderman" />
        <button class="close-btn">×</button>
        <div class="movie-info">
          <h3>The Amazing Spiderman</h3>
          <p>Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut...</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Secondsection',
  mounted() {
    const cards = this.$el.querySelectorAll('.movie-card');

    // Animate cards in on mount
    cards.forEach((card, i) => {
      card.style.opacity = '0';
      card.style.transform = 'translateY(40px) scale(0.97)';
      setTimeout(() => {
        card.style.transition = 'transform 0.7s cubic-bezier(.33,1.02,.54,.99), opacity 0.7s cubic-bezier(.33,1.02,.54,.99), box-shadow 0.25s cubic-bezier(.33,1.02,.54,.99)';
        card.style.opacity = '1';
        card.style.transform = 'translateY(0) scale(1)';
      }, 150 + i * 180);
    });

    // Use pointer events for all devices
    cards.forEach(card => {
      card.addEventListener('pointermove', (e) => {
        // Only animate for mouse or pen, not touch
        if (e.pointerType === 'mouse' || e.pointerType === 'pen') {
          const rect = card.getBoundingClientRect();
          const x = e.clientX - rect.left;
          const y = e.clientY - rect.top;
          const centerX = rect.width / 2;
          const centerY = rect.height / 2;
          const rotateX = ((y - centerY) / centerY) * -8;
          const rotateY = ((x - centerX) / centerX) * 8;
          card.style.transform = `scale(1.07) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
          card.style.zIndex = 3;
          card.style.boxShadow = "0 16px 40px 0 rgba(0,0,0,0.35)";
        }
      });
      card.addEventListener('pointerleave', () => {
        card.style.transform = "translateY(0) scale(1)";
        card.style.zIndex = "";
        card.style.boxShadow = "";
      });
    });
  }
}
</script>

<style scoped>
.movie-library {
  background: #111;
  color: #fff;
  padding: 2.5rem 0 0 0;
}
.movie-card {
  transition:
    transform 0.25s cubic-bezier(.33,1.02,.54,.99),
    box-shadow 0.25s cubic-bezier(.33,1.02,.54,.99),
    opacity 0.7s cubic-bezier(.33,1.02,.54,.99);
  will-change: transform;
  background: #222;
  border-radius: 8px;
  overflow: hidden;
  position: relative;
  flex: 1 1 33.3333%;
  min-width: 0;
  display: flex;
  flex-direction: column;
  max-width: none;
  /* Remove animation and opacity here, JS will handle it */
  perspective: 800px;
}

/* Remove transform from hover/focus so JS can control it */
.movie-card:hover,
.movie-card:focus-within {
  /* Only shadow and z-index for accessibility */
  box-shadow: 0 16px 40px 0 rgba(0,0,0,0.35);
  z-index: 3;
}

.library-header {
  padding: 2rem 2rem 1.5rem 2rem;
}
.library-header h1 {
  font-size: 4rem;
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 1.5rem;
  text-align: left;
}
.library-header p {
  font-size: 1.25rem;
  color: #b2c2c2;
  max-width: 700px;
  line-height: 1.5;
    text-align: left;

}
.library-favourites {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem 2rem 1rem 2rem;
}
.library-favourites h2 {
  font-size: 2rem;
  font-weight: 500;
  letter-spacing: 2px;
}
.search-form {
  display: flex;
  align-items: center;
}
.search-form input {
  font-size: 1.2rem;
  padding: 0.7rem 1.5rem;
  border: 2px solid #fff;
  border-radius: 4px;
  background: transparent;
  color: #fff;
  outline: none;
  width: 340px;
}
.search-form input::placeholder {
  color: #b2c2c2;
  font-size: 1.1rem;
}
hr {
  border: none;
  border-top: 3px solid #fff;
  margin: 0 2rem 2rem 2rem;
}
.movie-grid {
  display: flex;
  gap: 2rem;
  height: 90vh;
  width: 100vw;
  max-width: 100vw;
  margin-left: calc(-50vw + 50%);
  margin-right: 0;
  box-sizing: border-box;
  padding: 0 8vw 2rem 8vw;
}
.movie-card {
  background: #222;
  border-radius: 8px;
  overflow: hidden;
  position: relative;
  flex: 1 1 33.3333%;
  min-width: 0;
  display: flex;
  flex-direction: column;
  max-width: none;
  /* Remove animation and opacity here, JS will handle it */
  perspective: 800px;
  will-change: transform;
  transition:
    transform 0.25s cubic-bezier(.33,1.02,.54,.99),
    box-shadow 0.25s cubic-bezier(.33,1.02,.54,.99),
    opacity 0.7s cubic-bezier(.33,1.02,.54,.99);
}

.movie-card:hover,
.movie-card:focus-within {
  /* Only shadow and z-index for accessibility */
  box-shadow: 0 16px 40px 0 rgba(0,0,0,0.35);
  z-index: 3;
}

/* Optional: smooth back to normal on mouse leave */
.movie-card {
  --tilt-x: 0deg;
  --tilt-y: 0deg;
}

.movie-card:nth-child(1) {
  animation-delay: 0.1s;
}
.movie-card:nth-child(2) {
  animation-delay: 0.3s;
}
.movie-card:nth-child(3) {
  animation-delay: 0.5s;
}

@keyframes cardFadeIn {
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
.movie-card img {
  width: 100%;
    height: 60vh;

  aspect-ratio: 16/11;
  object-fit: cover;
  display: block;
  flex-shrink: 0;
}

.movie-info {
  background: #444;
  padding: 1.5rem 1.2rem 1.2rem 1.2rem;
  color: #fff;
    height: 90vh;

  display: block;
}
.movie-info h3 {
  font-size: 1.8rem;
  font-weight: 600;
  margin: 0 0 0.7rem 0;
  letter-spacing: 1px;
  font-family: 'Poppins', sans-serif;
}
.movie-info p {
  font-size: 1.1rem;
  color: #e0dede;
  margin: 0;
  font-family: 'Poppins', sans-serif;
  line-height: 1.5;
  
  overflow: hidden;
}
.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0,0,0,0.6);
  color: #fff;
  border: none;
  font-size: 1.5rem;
  border-radius: 4px;
  cursor: pointer;
  padding: 0.2rem 0.7rem;
  z-index: 2;
  transition: background 0.2s;
}
.close-btn:hover {
  background: #ff4081;
}
@media (max-width: 900px) {


  .movie-card {
  background: #222;
  border-radius: 8px;
  overflow: hidden;
  position: relative;
  flex: 1 1 33.3333%;
  min-width: 0;
  display: flex;
  flex-direction: column;
  max-width: none;
  /* Remove animation and opacity here, JS will handle it */
  perspective: 800px;
  will-change: transform;
  transition:
    transform 0.25s cubic-bezier(.33,1.02,.54,.99),
    box-shadow 0.25s cubic-bezier(.33,1.02,.54,.99),
    opacity 0.7s cubic-bezier(.33,1.02,.54,.99);
}

/* Remove transform from hover/focus so JS can control it */
.movie-card:hover,
.movie-card:focus-within {
  /* Only shadow and z-index for accessibility */
  box-shadow: 0 16px 40px 0 rgba(0,0,0,0.35);
  z-index: 3;
}
  
  .library-header h1 {
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 2px;
  margin-bottom: 1.5rem;
  text-align: left;
}
.library-header p {
  font-size: 1.25rem;
  color: #b2c2c2;
  max-width: 700px;
  line-height: 1.5;
    text-align: left;

}
  
  .movie-grid {
    flex-direction: column;
    gap: 1.5rem;
    width: 100%;
    max-width: 100%;
    padding-left: 1rem;
    padding-right: 1rem;
    padding-bottom: 2rem;
    height: auto;
    margin-left: 0;
    
  }
  .movie-card {
    width: 100%;
    max-width: 100%;
    min-width: 0;
    height: auto;

    
    
  }
  .movie-card img {
    height: 45vw;
    min-height: 220px;
    max-height: 340px;
  }
  .movie-info {
    height: auto;
    padding: 1.2rem 1rem 1rem 1rem;
  }


  .library-header,
  .library-favourites,
  hr {
    padding-left: 1rem;
    padding-right: 1rem;
  }
  .library-favourites {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
    padding-left: 1rem;
    padding-right: 1rem;
    padding-top: 1.5rem;
    padding-bottom: 0.5rem;
  }
  .library-favourites h2 {
    font-size: 1.4rem;
    font-weight: 500;
    letter-spacing: 2px;
    margin-bottom: 0.5rem;
    text-align: left;
    width: 100%;
  }
  .search-form {
    width: 100%;
    margin-top: 0.5rem;
  }
  .search-form input {
    width: 100%;
    font-size: 1.1rem;
    padding: 0.7rem 1.5rem 0.7rem 2.5rem;
    background: transparent;
    border: 2px solid #fff;
    border-radius: 4px;
    color: #fff;
    outline: none;
    box-sizing: border-box;
    background-image: url("data:image/svg+xml,%3Csvg width='18' height='18' viewBox='0 0 18 18' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Ccircle cx='8.5' cy='8.5' r='6.5' stroke='%23b2c2c2' stroke-width='2'/%3E%3Cpath d='M16 16L13 13' stroke='%23b2c2c2' stroke-width='2' stroke-linecap='round'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: 0.7rem center;
  }
}
</style>
