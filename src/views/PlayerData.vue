<template>
  <div class="hero-container">
    <div class="player-data">
      <h1>Player Data</h1>
      <h2>Search for player data across all sports and leagues</h2>
    </div>
    <input
      type="text"
      v-model="searchedPlayer"
      @keypress.enter="fetchPlayerData"
      placeholder="Search for a player"
      class="searchbar"
    />
    <ul v-if="playerData" class="player-info">
      <li><strong>Name:</strong> {{ playerData.strPlayer }}</li>
      <li><strong>Date of birth:</strong> {{ playerData.dateborn }}</li>
      <li><strong>Nationality:</strong> {{ playerData.strNationality }}</li>
      <li><strong>Current Team:</strong> {{ playerData.strTeam }}</li>
      <li><strong>Wage:</strong> {{ playerData.strWage }}</li>
    </ul>
    <div v-else class="no-player">
      We can't seem to find that specific player, try entering another one!
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const searchedPlayer = ref('')
const playerData = ref(null)

async function fetchPlayerData() {
  if (searchedPlayer.value.trim() === '') {
    playerData.value = null
    return
  }

  try {
    const response = await fetch(
      `https://www.thesportsdb.com/api/v1/json/3/searchplayers.php?p=${encodeURIComponent(searchedPlayer.value)}`
    )
    const data = await response.json()
    playerData.value = data?.player?.[0] ?? null
  } catch (error) {
    console.error('There was an error fetching player data:', error)
    playerData.value = null
  }
}
</script>

<style scoped>
.hero-container {
  position: relative;
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
  overflow: hidden;
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

.player-data {
  position: relative;
  text-align: center;
}

h1,
h2 {
  color: #fff;
  z-index: 1;
}

h1 {
  position: relative;
  top: 0;
}

h2 {
  position: relative;
  top: 10px;
}

.player-info {
  list-style: none;
  color: #fff;
}

.player-info,
.searchbar,
.no-player {
  z-index: 1;
}

.no-player {
  color: #fff;
}
</style>
