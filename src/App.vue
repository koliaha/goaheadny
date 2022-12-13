<template>
  <div id="app">
    <let-it-snow v-bind="snowConf" :show="show"></let-it-snow>
    <div class="main-wrapp">
      <MainBox />
    </div>
  </div>
</template>

<script>
import MainBox from './components/MainBox.vue'

export default {
  name: 'App',
  components: {
    MainBox
  },
  data() {
    return {
      snowConf: {
        windPower: 1,
        speed: 3,
        count: 12,
        size: 10,
        opacity: 1,
        images: ['https://raw.githubusercontent.com/bob-chen/let_it_snow/master/demo/snow.png',
          'https://raw.githubusercontent.com/bob-chen/let_it_snow/master/demo/sock.png',
          'https://raw.githubusercontent.com/bob-chen/let_it_snow/master/demo/tree.png']
      },
      show: false
    }
  },
  mounted() {
    this.show = true
    //   setTimeout( () => {
    //       this.show = false
    //   }, 5000)

    //   setTimeout( () => {
    //       this.show = true
    //   }, 10000)      
  }
}
</script>

<style lang="scss">
@import url(@/assets/fonts/fonts.scss);

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: black;
}

#app {
  font-family: Museo Sans Cyrl;
  color: #ffffff;

}

a {
  color: inherit;
  text-decoration: none;
}

.main-wrapp {
  min-height: 100vh;
  background: black;
}

.container {
  max-width: 1290px;
  width: 100%;
  margin: 0 auto;
  @media screen and (max-width:1325px){
    max-width: 1090px;
  }
  @media screen and (max-width:1125px){
    max-width: 920px;
  }
  @media screen and (max-width:940px){
    max-width: 750px;
  }
  @media screen and (max-width:750px){
    max-width: 620px;
    padding: 0 15px;
  }
}
::-webkit-scrollbar {
  width: 12px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #ff7323;
  border-radius: 5px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #ff863f;
}
</style>
