<template>
  <div class="bros">
    <img class="bros__bro" :src="this.images.whiteBro" alt="">
    <img class="bros__bro" :src="this.images.blackBro" alt="">
  </div>
</template>
<script>
export default {
  name: 'Characters',
  data() {
    return {
      animaaiclass: 'animaii',
      animaai: '',
      animeDelay: 1500,
      totalHeight: 0,
      images: {
        blackBro: require('@/assets/black-bro_mercenary.png'),
        whiteBro: require('@/assets/white-bro_finalFight.png')
      }
    }
  },
}
</script>
<style lang="scss" scoped>
.bros {
  display: flex;
  justify-content: space-between;
  &__bro {
    max-width: 500px;
    
  }
}
</style>