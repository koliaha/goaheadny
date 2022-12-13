<template>
  <div>
    <div class="main-wrapper">
      <LetSnow />
      <HeaderMain />
      <MainTree />
      <div class="snow_bg"></div>
    </div>
    <AdSlider />
    <FooterMain />
  </div>
</template>
  
<script>
import HeaderMain from './HeaderMain.vue'
import FooterMain from './FooterMain.vue'
import AdSlider from './AdSlider.vue'
import MainTree from './MainTree.vue'
import LetSnow from './LetSnow.vue'

export default {
  name: 'MainBox',
  components: {
    FooterMain, HeaderMain, MainTree, AdSlider, LetSnow
  }
}
</script>
  
<style lang="scss">
.main-wrapper {
  padding-bottom: 85px;
  position: relative;

  &::before,
  &::after {
    content: '';
    position: absolute;
    max-width: 50%;
    width: 100%;
    min-height: 1000px;
    height: 100%;
    top: 0;
    z-index: 3;
  }

  &::before {
    background: url('@/assets/img/bgleft.png');
    background-size: 100% auto;
    background-repeat: no-repeat;
    background-position: top;
    left: 0;
  }

  &::after {
    background: url('@/assets/img/bgright.png');
    background-size: 100% auto;
    background-repeat: no-repeat;
    background-position: top;
    right: 0;
  }

  @media screen and (max-width:650px) {
    &::before,&::after {
      background-size: auto 100% ;
    }
  }
}

.snow_bg {
  position: absolute;
  bottom: 0;
  max-height: 752px;
  width: 100%;
  height: 100%;
  left: 0;
  z-index: 0;
  background: url('@/assets/img/snowbg.png');
  background-size: auto 100%;
  background-repeat: no-repeat;
  background-position: bottom;

  @media screen and (max-width:650px) {
    background-size: 100% auto;
  }
}
</style>
  