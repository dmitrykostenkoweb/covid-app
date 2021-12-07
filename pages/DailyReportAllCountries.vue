<template>
  <div class="wrapper">
    <h1>All Countries</h1>
    <div v-for="(value, key, idx) in covidData[0]" :key="idx">
      <ul>
        <li class="flex-wrapper">
          <p class="sub-title">{{ key.toUpperCase() }}:</p>
          <span>{{ value }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data() {
    return {
      covidData: [],
      covidDataTest: [
        {
          country: 'Poland',
          code: 'PL',
          confirmed: 3704040,
          recovered: 3184676,
          critical: 2036,
          deaths: 86205,
          latitude: 51.919438,
          longitude: 19.145136,
          lastChange: '2021-12-07T10:53:51+01:00',
          lastUpdate: '2021-12-07T20:00:04+01:00',
        },
      ],
    }
  },
  mounted() {
    this.getData()
  },
  methods: {
    async getData() {
      const options = {
        method: 'GET',
        url: 'https://covid-19-data.p.rapidapi.com/report/country/all',
        params: { date: '2020-04-01' },
        headers: {
          'x-rapidapi-host': 'covid-19-data.p.rapidapi.com',
          'x-rapidapi-key':
            '2b55623403msh1f39cbf2fa1661ep100c15jsnb35dabe2958c',
        },
      }

      await axios
        .request(options)
        .then((response) => {
          response.data.forEach((dataItem) => {
            this.covidData.push(dataItem)
          })

          console.log(this.covidData[0])
        })
        .catch((error) => {
          console.error(error)
        })
    },
  },
}
</script>

<style>
body {
  font-family: 'Montserrat Alternates', sans-serif;
}
.sub-title {
  font-weight: 600;
  color: grey;
}

.flex-wrapper {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: 20px;
}
</style>
