<template>
  <footer class="site-footer">
    <div class="footer-content">
      <div class="footer-title">Movie World</div>
      <div class="footer-address">Amadeus IT Group, S.A., Madrid, Spain</div>
     
      <div class="footer-copyright">&copy; {{ new Date().getFullYear() }} Movie World. All rights reserved.</div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.site-footer { background: #222; color: #fff; padding: 2rem 1rem; text-align: center; }
.footer-title { font-size: 1.5rem; font-weight: bold; margin-bottom: 0.5rem; }
.footer-address { margin-bottom: 1rem; }
.footer-social img { width: 28px; margin: 0 0.5rem; vertical-align: middle; }
.footer-copyright { margin-top: 1rem; font-size: 0.95rem; color: #aaa; }
</style>
