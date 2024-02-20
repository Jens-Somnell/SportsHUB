<template>
  <nav>
    <div class="hamburger-menu" @click="toggleMenu">
      <div class="line" v-bind:class="{ active: isMenuOpen }"></div>
      <div class="line" v-bind:class="{ active: isMenuOpen }"></div>
      <div class="line" v-bind:class="{ active: isMenuOpen }"></div>
    </div>

    <ul class="dropdown-menu" v-bind:class="{ active: isMenuOpen }">
      <li><RouterLink @click="closeDropdown" to="/" class="navbar-link">Home</RouterLink></li>
      <li>
        <RouterLink @click="closeDropdown" to="/playerdata" class="navbar-link">Player Data</RouterLink>
      </li>
    </ul>

    <RouterLink @click="closeDropdown" to="/" class="sportshub-link">SportsHUB</RouterLink>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeDropdown = () => {
  isMenuOpen.value = false
}
</script>

<style scoped>
nav {
  background-color: #097509;
  color: #fff;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  z-index: 1;
}

.hamburger-menu {
  cursor: pointer;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  width: 32px;
  height: 20px;
}

.line {
  width: 100%;
  height: 3px;
  background-color: #fff;
  transition: all 0.3s ease;
}

.active {
  background-color: #fff;
}

.dropdown-menu {
  position: absolute;
  top: calc(100% + 10px);
  left: 0;
  background-color: #097509;
  list-style-type: none;
  padding: 0;
  margin: 0;
  width: 225px;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease;
}

.dropdown-menu li {
  padding: 8px 16px;
  margin: 4px 0;
  border-bottom: 1px solid #fff;
}

.dropdown-menu li:last-child {
  border-bottom: none;
}

.dropdown-menu.active {
  opacity: 1;
  pointer-events: auto;
}

.sportshub-link {
  color: #fff;
  text-decoration: none;
  font-size: 32px;
}

.navbar-link {
  color: #fff;
  text-decoration: none;
  font-size: 20px;
}
</style>
