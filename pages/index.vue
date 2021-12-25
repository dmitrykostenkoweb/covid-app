<template>
  <div class="app">
    <live-background />
    <div class="content__z-index">
      <h1>COVID INFO</h1>
      <warning-dialog v-if="dialog">{{ dialog }}</warning-dialog>
      <my-select @selectedCountry="getCountry" :dialog="dialog" />

      <div class="data__wrapper">
        <div class="data" v-for="(data, idx) in covidData" :key="idx">
          <div class="country-name__wrapper">
            <h2 class="country-name">{{ data.country }}</h2>
            <img
              class="country-name-img"
              :src="`https://countryflagsapi.com/png/${countryList[idx]}`"
            />
          </div>

          <div class="data-item">
            <p style="color: red" class="data-item-key">Deaths:</p>
            <span class="data-item-value">{{ data.deaths }}</span>
          </div>

          <div class="data-item">
            <p style="color: orange" class="data-item-key">Critical:</p>
            <span class="data-item-value">{{ data.critical }}</span>
          </div>

          <div class="data-item">
            <p style="color: yellow" class="data-item-key">Confirmed:</p>
            <span class="data-item-value">{{ data.confirmed }}</span>
          </div>

          <div class="data-item">
            <p style="color: green" class="data-item-key">Recovered:</p>
            <span class="data-item-value">{{ data.recovered }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import MySelect from '../components/my-select.vue'
import LiveBackground from '../components/LiveBackground.vue'
import WarningDialog from '../components/WarningDialog.vue'
export default {
  components: { MySelect, LiveBackground, WarningDialog },
  data() {
    return {
      country: '',
      countryList: [],
      covidData: [],
      dialog: '',
    }
  },
  watch: {
    country() {
      this.getData()
    },
  },
  mounted() {},
  methods: {
    getCountry(country) {
      if (this.countryList.includes(country)) {
        this.dialog = 'You already have this country!'
        this.removeDialog()
      } else {
        this.country = country
        this.countryList.push(country)
      }
    },
    async getData() {
      const options = {
        method: 'GET',
        url: 'https://covid-19-data.p.rapidapi.com/country',
        params: { name: `${this.country}`, format: 'json' },
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
        })
        .catch((error) => {
          alert(error)
        })
        .finally((this.dialog = ''))
    },

    removeDialog() {
      setTimeout(() => {
        this.dialog = ''
      }, 5000)
    },
  },
}
</script>
MySelect
<style>
.app {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100vh;
  width: 100vw;
}
h1 {
  margin: 20px auto;
  text-align: center;
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

.data__wrapper {
  width: 100%;
  padding: 16px;
  justify-content: space-around;
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}
.data {
  width: max-content;
  border: 1px solid white;
  border-radius: 4px;
  padding: 16px;
  flex-basis: 20%;
}
.data-item {
  display: flex;
  gap: 8px;
  flex-wrap: nowrap;
  align-items: center;
}
.data-item-key {
  display: flex;
  flex-wrap: nowrap;
  font-size: 12px;
}
.data-item-value {
  display: flex;
  flex-wrap: nowrap;
  font-size: 14px;
  font-weight: 600;
}

.country-name__wrapper {
  display: flex;
  gap: 8px;
}
.country-name {
}
.country-name-img {
  width: 30px;
  border-radius: 50%;
  box-shadow: 10px 10px 10px black;
}
</style>
