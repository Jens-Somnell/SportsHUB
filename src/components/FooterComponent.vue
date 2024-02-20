<template>
  <footer>
    <div class="footer-content">
      <p>&copy; {{ footerText  }}</p>
      <nav>
        <RouterLink to="/" class="footer-link">Home</RouterLink>
        <RouterLink to="/playerdata" class="footer-link">Player Data</RouterLink>
      </nav>
    </div>
  </footer>
</template>

<script setup>
defineProps({
  footerText: String
})
</script>

<style scoped>
footer {
  background-color: #097509;
  color: #fff;
  padding: 20px 0;
  text-align: center;
  width: 100%;
  bottom: 0;
  position: sticky;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
}

nav {
  margin-top: 10px;
  display: flex;
  justify-content: left;
}

.footer-link {
  margin: 0 12px;
}

nav a {
  color: #fff;
  margin: 0 px;
  text-decoration: none;
}

nav a:hover {
  text-decoration: underline;
}
</style>
