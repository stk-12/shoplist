<template>
  <div id="app">
    <div class="shopList">
      <div class="area">
        <h2>北海道</h2>
        <ul class="shoplist">
          <li v-for="info in filteredHokkaido">
            <p class="shop">{{ info.shop }}</p>
            <p class="tel">{{ info.tel }}</p>
            <div class="add">
              <p class="postal">{{ info.postal }}</p>
              <p class="address">{{ info.address }}</p>
            </div>
          </li>
        </ul>
      </div>
      <div class="area">
        <h2>青森県</h2>
        <ul class="shoplist">
          <li v-for="info in filteredAomori">
            <p class="shop">{{ info.shop }}</p>
            <p class="tel">{{ info.tel }}</p>
            <div class="add">
              <p class="postal">{{ info.postal }}</p>
              <p class="address">{{ info.address }}</p>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
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
  },
  computed: {
    filteredHokkaido: function(){
      return this.informations.filter(function(info){
        return info.prefectures === "北海道"
      })
    },
    filteredAomori: function(){
      return this.informations.filter(function(info){
        return info.prefectures === "青森県"
      })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
h2 {
  background: #000;
  color: #fff;
  padding: 10px 25px;
}
.shoplist {
  list-style: none;
  margin: 0;
  padding: 0;
  li {
    padding: 20px 25px;
    border-bottom: 1px solid #aaa;
    &:last-child {
      border: none;
    }
  }
}
</style>
