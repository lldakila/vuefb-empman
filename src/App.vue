<template>
  <div id="app">
    <Navbar />
    <!-- <Test /> -->
    <div class="container">
      <router-view/>
    </div>
  </div>

</template>

<script>
import Navbar from './components/Navbar'
// import Test from './components/Test'


export default {
  name: 'app',
  components: {
    Navbar
    // Test
  }
}
</script>

<style>
nav {
  margin-bottom: 10px;
}
</style>


