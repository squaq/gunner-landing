<template>
  <div class="tv" :style="{'background-image':'url('+this.images.mainBg+')'}">
    <Characters/>
  </div>
</template>


<script>
import Characters from './Characters.vue'
export default {
  name: 'TvScreen',
  components: {
    Characters
  },
  data() {
    return {
      animaaiclass: 'animaii',
      animaai: '',
      animeDelay: 1500,
      totalHeight: 0,
      images: {
        mainBg: require('@/assets/jungle_pixelart.png')
      }
    }
  },
}
</script>
<style lang="scss" scoped>
.tv {
  background-size: cover center;

}
</style>