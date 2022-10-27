<template>
  <div class="home">
    <h1 class="home-title">Weather in your city</h1>
    <form class="home-form" @submit="weather">
      <label class="city" for="city">City</label>
      <li class="message__form" v-show="this.alertMsg">{{ this.alertMsg }}</li>
      <li class="message__form" v-show="this.error">{{ this.error }}</li>
      <input type="text" id="city" placeholder="Enter a city name" v-model="city">
      <button class="btn-send">
        <fa class="fa" icon="fa fa-search" />
      </button>
    </form>
    <Weather :datas="datas" />
  </div>
</template>

<script>
import api from '../../service/api.js'
import Weather from '../../components/Weather/Weather.vue'

export default {
  name: 'Home',

  components: {
    Weather
  },

  data() {
    return {
      datas: {},
      city: '', //|| this.$route.params.city,
      alertMsg: '',
      units: 'metric',
      error: '',
    }
  },

  methods: {
    async weather(event) {
      event.preventDefault()

      if (this.city == '' || this.city == ' ') {
        this.alertMsg = "Can't be empty"

        setTimeout(() => {
          this.alertMsg = ''
        }, 5000)
      } else {
        const city = this.city.replaceAll(' ', '%20')
        const url = `${api}&q=${city}&units=${this.units}`
        await fetch(url).then(res => {
          res.json().then(datas => {
            if (datas.cod == '404') {
              this.error = datas.message
              setTimeout(() => {
                this.error = ''
              }, 5000)
            }

            console.log(`Status: ${datas.cod}`)

            this.datas = {
              name: datas.name,
              country: datas.sys.country,
              sunrise: this.formatTime(datas.sys.sunrise),
              sunset: this.formatTime(datas.sys.sunset),
              lat: datas.coord.lat,
              lon: datas.coord.lon,
              temp_now: parseInt(datas.main.temp),
              temp_max: parseInt(datas.main.temp_max),
              temp_min: parseInt(datas.main.temp_min),
              desc: datas.weather[0].description,
              icon: `https://openweathermap.org/img/wn/${datas.weather[0].icon}@4x.png`,
              humidity: datas.main.humidity
            }
          })

        })
      }
    },

    formatTime(formatUnix) {
      let date = new Date(formatUnix * 1000)
      let hours = date.getHours()
      let minutes = date.getMinutes()

      if (hours <= 9) hours = '0' + hours
      if (minutes <= 9) minutes = '0' + minutes

      return `${hours}:${minutes}`
    }
  },

  created() {
    document.title = 'Home'
  }
}
</script>

<style src="./style.sass" lang="sass" scoped/>