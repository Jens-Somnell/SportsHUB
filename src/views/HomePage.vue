<template>
  <div class="hero-container">
    <h1>SportsHUB</h1>
    <p>Elevate Your Game!</p>
  </div>
</template>

<style scoped>
.hero-container {
  width: 100%;
  height: calc(100vh - 165px);
  background-image: url('../assets/hero-image.jpg');
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 20px;
}

.hero-container::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.8);
}

h1 {
  margin: 0;
  color: #fff;
  z-index: 1;
}

p {
  margin: 0;
  color: #fff;
  z-index: 1;
}
</style>
