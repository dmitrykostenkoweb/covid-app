<template>
  <header class="header container">
    <nav class="nav">
      <div class="nav-item-wrapper">
        <h2>Daily Report</h2>
        <NuxtLink
          class="nav-item"
          :to="{
            name: 'DailyReportAllCountries',
          }"
        >
          All Countries</NuxtLink
        >
        <NuxtLink
          class="nav-item"
          :to="{
            name: 'DailyReportByCountryName',
          }"
        >
          Country By Name</NuxtLink
        >
      </div>
      <div class="nav-item-wrapper">
        <h2>Latest</h2>

        <NuxtLink
          class="nav-item"
          :to="{
            name: 'LatestAllCountries',
          }"
        >
          All Countries</NuxtLink
        >
        <NuxtLink
          class="nav-item"
          :to="{
            name: 'LatestCountryDataByName',
          }"
        >
          Country By Name</NuxtLink
        >
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'AppBar',
  data() {
    return {
      navItems: ['Top Rated', 'Popular', 'Now Playing'],
    }
  },
  methods: {},
}
</script>

<style scoped>
.header {
  position: absolute;
  top: 10%;
  left: 0;
  width: 100%;
  margin: 0 auto;
  padding: 10px;
}
.nav {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 20px;
  margin-top: 20px;
}
.nav-item-wrapper {
  background-color: rgba(255, 255, 255, 0.3);
  padding: 10px;
  margin: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 10px;
  border: 1px solid rgba(128, 128, 128, 0.3);
  border-radius: 20px;
}
.nav-item {
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  font-size: 20px;
  color: rgb(19, 19, 19);
}
</style>
