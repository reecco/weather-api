<template>
  <div class="about">
    <h1 class="about-title">About</h1>
    <p class="about-text">Built with 
      <a class="link" href="https://openweathermap.org/" target="_blank">OpenWeather API</a>.
      </p>
    <div class="about-box">
      <h3 class="box-title">Repository</h3>
      <a class="link" href="https://github.com/fredcardoso191/weather-api" target="_blank">
        <img class="link-icon" src="@/assets/images/github.png" alt="GitHub Image">
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'About',

  created() {
    document.title = 'About'
  }
}
</script>

<style src="./style.sass" lang="sass" scoped/>
