<template>
  <nav
    class="navbar navbar-light navbar-dark"
    style="background-color: #3d0427"
  >
    <a class="navbar-brand" id="logo" href="#">
      <img :src="logo" width="180" alt="" />
    </a>
  </nav>
</template>
<script>
import logo from '~/assets/Logo.svg'
export default {
  data() {
    return {
      logo: logo,
    }
  },
}
</script>
<style scoped>
nav {
  margin: 0px 10%;
  padding: 0;
}
#logo {
  padding: 20px 0;
}
</style>
