<template>
  <header class="main-header" :data-hide="hideHeader.toString()">
    <div class="logo-area">
      <img src="../assets/Logos/Logo White.svg" alt="Logoipsum" class="logo-img" />
    </div>
    <nav class="main-nav" :class="{ open: navOpen }" aria-label="Main Navigation">
      <button
        class="menu-icon"
        aria-label="Toggle navigation"
        @click="navOpen = !navOpen"
        :aria-expanded="navOpen.toString()"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
      <ul>
        <li><a href="#home">HOME</a></li>
        <li><a href="#screens">OUR SCREENS</a></li>
        <li><a href="#schedule">SCHEDULE</a></li>
        <li><a href="#library"><u>MOVIE LIBRARY</u></a></li>
        <li><a href="#contact">LOCATION & CONTACT</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      navOpen: false,
      lastScrollY: 0,
      hideHeader: false
    }
  },
  watch: {
    // Close nav on route change (optional for SPA)
    $route() {
      this.navOpen = false;
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll, { passive: true });
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const currentY = window.scrollY;
      if (currentY > this.lastScrollY && currentY > 60) {
        this.hideHeader = true; // scrolling down, hide
      } else {
        this.hideHeader = false; // scrolling up, show
      }
      this.lastScrollY = currentY;
    }
  }
}
</script>

<style scoped>
.main-header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem 1rem 2rem;
  background: #000;
  color: #fff;
  border-bottom: 2px solid #fff;
  box-sizing: border-box;
  transition: transform 1.25s cubic-bezier(.33,1.02,.54,.99), opacity 0.25s;
}
.main-header[data-hide="true"] {
  transform: translateY(-100%);
  opacity: 0;
  pointer-events: none;
}
.logo-area {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  min-width: 80px;    /* Add a minimum width */
  padding-right: 2rem; /* Add space between logo and nav */
}
.logo-img {
  height: 48px;
  width: 148px;
}
.logo-text {
  font-size: 2rem;
  font-weight: bold;
  color: #fff;
  letter-spacing: 1px;
}
.main-nav {
  display: flex;
  align-items: center;
  gap: 2rem;
  position: relative;
}
.main-nav ul {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}
.main-nav a {
  color: #fff;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 500;
  letter-spacing: 1px;
  transition: color 0.2s;
}
.main-nav a:hover, .main-nav a:focus {
  color: #ffcc00;
}
.menu-icon {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  margin-left: 2rem;
  cursor: pointer;
  background: none;
  border: none;
  padding: 0;
}
.menu-icon span {
  display: block;
  width: 32px;
  height: 3px;
  background: #fff;
  border-radius: 2px;
  transition: all 0.3s;
}

/* Responsive styles */
@media (max-width: 900px) {
  .main-header {
    flex-direction: row;
    align-items: center;
    padding: 1rem;
  }
  .logo-img {
    height: 36px;
    width: 136px;
  }
  .logo-text {
    font-size: 1.3rem;
  }
  .main-nav {
    flex-direction: column;
    align-items: flex-end;
    gap: 0;
  }
  .main-nav ul {
    flex-direction: column;
    gap: 0.5rem;
    background: #111;
    position: absolute;
    top: 60px;
    right: 0;
    min-width: 180px;
    border-radius: 0 0 8px 8px;
    box-shadow: 0 8px 24px rgba(0,0,0,0.25);
    padding: 1rem 1.5rem;
    display: none;
    transition: right 0.3s;
  }
  .main-nav.open ul {
    display: flex;
  }
  .menu-icon {
    display: flex;
  }
}

/* Sidebar for mobile */
@media (max-width: 600px) {
  .main-header {
    padding: 0.7rem 0.7rem 0.7rem 1rem;
  }
  .main-nav ul {
    position: fixed;
    top: 0;
    right: -100vw;
    height: 100vh;
    width: 50vw;           /* Sidebar takes half the screen width */
    min-width: 180px;
    max-width: 100vw;
    background: #111;
    border-radius: 0;
    padding: 2.5rem 1.5rem 1.5rem 2rem;
    flex-direction: column;
    gap: 1.5rem;
    z-index: 2000;
    transition: right 0.3s;
    display: flex;
  }
  .main-nav.open ul {
    right: 0;
    display: flex;
  }
  .menu-icon {
    display: flex;
    z-index: 2100;
  }
}

/* Sidebar for tablet */
@media (max-width: 900px) and (min-width: 601px) {
  .main-nav ul {
    position: fixed;
    top: 0;
    right: -100vw;
    height: 100vh;
    width: 50vw;           /* Sidebar takes half the screen width */
    min-width: 220px;
    max-width: 100vw;
    background: #111;
    border-radius: 0;
    padding: 2.5rem 1.5rem 1.5rem 2rem;
    flex-direction: column;
    gap: 1.5rem;
    z-index: 2000;
    transition: right 0.3s;
    display: flex;
  }
  .main-nav.open ul {
    right: 0;
    display: flex;
  }
  .menu-icon {
    display: flex;
    z-index: 2100;
  }
}

@media (max-width: 321px) {
  .main-header {
    padding: 0.5rem 0.3rem 0.5rem 0.5rem;
  }
  .logo-area {
    min-width: 60px;
    padding-right: 0.5rem;
    gap: 0.4rem;
  }
  .logo-img {
    height: 24px;
    width: 120px;
  }
  .logo-text {
    font-size: 0.9rem;
  }
  .main-nav ul {
    min-width: 100px;
    padding: 1rem 0.5rem;
    font-size: 0.95rem;
  }
  .menu-icon span {
    width: 22px;
    height: 2px;
  }
}
</style>