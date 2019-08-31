<template>
  <div id="app">
    <div class="shopList">
      <div class="area">
        <ul>
          <li v-for="(information, index) in informations" :key="index">
            <p class="shop">{{ information.shop }}</p>
            <p class="tel">{{ information.tel }}</p>
            <div class="add">
              <p class="postal">{{ information.postal }}</p>
              <p class="address">{{ information.address }}</p>
            </div>
          </li>
        </ul>
        <pre>{{ $data }}</pre>
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  // components: {
  //   HelloWorld
  // }
  data () {
    return {
      informations: null
    }
  },
  created() {
    var vm = this
    this.$axios
      .get('./shop.json')
      .then(function (response){
        vm.informations = response.data
      })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
