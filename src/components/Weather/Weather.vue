<template>
  <div class="result" v-show="datas.name">
    <h3 class="result-infos__title">{{ datas.name }}, {{ datas.country }} weather</h3>
    <div class="result-infos__sky">
      <label class="title-sky">{{ datas.desc }}</label>
      <img class="sky-icon" :src="datas.icon" :alt="`${datas.desc} icon`">
    </div>
    <div class="result-infos__main">
      <div class="result-infos__temp">
        <div class="infos">
          <div class="infos-box">
            <label class="category">Now</label>
            <fa class="fa" icon="fa-solid fa-temperature-half" />
          </div>
          <p class="temp temp_now">{{ datas.temp_now }}°C</p>
        </div>
        <div class="infos">
          <div class="infos-box">
            <label class="category">Max</label>
            <fa class="fa" icon="fa-solid fa-temperature-arrow-up" />
          </div>
          <p class="temp temp_max">{{ datas.temp_max }}°C</p>
        </div>
        <div class="infos">
          <div class="infos-box">
            <label class="category">Min</label>
            <fa class="fa" icon="fa-solid fa-temperature-arrow-down" />
          </div>
          <p class="temp temp_min">{{ datas.temp_min }}°C</p>
        </div>
      </div>
      <div class="result-infos__others">
        <div class="infos-sun">
          <div class="sun">
            <div class="box">
              <label class="box-title">Sunrise</label>
              <span class="box-icon sunrise"></span>
            </div>
            <p class="sun-text">{{ datas.sunrise }}</p>
          </div>
          <div class="sun">
            <div class="box">
              <label class="box-title">Sunset</label>
              <span class="box-icon sunset"></span>
            </div>
            <p class="sun-text">{{ datas.sunset }}</p>
          </div>
        </div>
        <div class="infos__air">
          <div class="air-humidity">
            <div class="box">
              <label class="box-title">Humidity</label>
              <span class="box-icon humidity"></span>
            </div>
            <p class="info-text">{{ datas.humidity }}%</p>
          </div>
        </div>
      </div>
      <div class="result-infos__local">
        <div class="coord lat">
          <label class="coord-title">Latitude</label>
          <p class="coord-value">{{ datas.lat }}</p>
        </div>
        <div class="coord lon">
          <label class="coord-title">Longitude</label>
          <p class="coord-value">{{ datas.lon }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Weather',

  props: {
    datas: Object
  }
}
</script>

<style src="./style.sass" lang="sass" scoped/>