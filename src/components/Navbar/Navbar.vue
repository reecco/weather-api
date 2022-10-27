<template>
  <div>
    <div class="logo">
      <router-link to="/">
        <div class="logo-image"></div>
      </router-link>
      <a class="logo-title" href="/">Weather</a>
    </div>
    <nav class="nav">
      <router-link to="/" class="nav-link">Home</router-link>
      <router-link to="/about" class="nav-link">About</router-link>
    </nav>
    <button class="menu" @click="menu">
      <fa class="icon" icon="fa-solid fa-bars" />
    </button>
  </div>
  <div class="nav-collapse">
    <a href="/" class="link">Home</a>
    <a href="/about" class="link">About</a>
  </div>
</template>

<script>

export default {
  name: 'Navbar',

  methods: {
    menu() {
      let buttonMenu = document.querySelector('.menu')
      let menu = document.querySelector('.nav-collapse')

      let menuActive = menu.classList.toggle('nav-collapse--active')

      buttonMenu.addEventListener('click', () => menuActive)
    }
  }
}
</script>

<style src="./style.sass" lang="sass" scoped/>