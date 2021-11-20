<template>
  <div class="gunner">
    <div class="gunner__bg" :class="animaai" >
      <img ref="mamai" class="gunner__bg--blur"  :src="images.mainBg">
      <div class="gunner__bg--blur-2" :style="{'height':this.totalHeight+'px'}"></div>
      <div class="gunner__bg--lines"  ></div><!-- v-if="animaai !== ''" -->
    </div>    
  </div>
</template>

<script>
export default {
  name: 'MainGunner',
  props: {
    msg: String
  },
  data() {
    return {
      animaaiclass: 'animaii',
      animaai: '',
      animeDelay: 1500,
      totalHeight: 0,
      images: {
        mainBg: require('@/assets/sketch-test.png')
      }
    }
  },
  created() {
    this.addAnimaii()
  },
  mounted() {
    console.log('mounted', this.$refs.mamai.clientHeight)
    this.totalHeight = this.$refs.mamai.clientHeight;
  },
  methods: {
    addAnimaii() {
      console.log('addAnimaii')
      setTimeout(() => {
        this.animaai = this.animaaiclass;
        this.removeAnimaii();
    }, this.animeDelay);
    },

    removeAnimaii() {
      setTimeout(() => {
        this.animaai = '';
        this.addAnimaii();
    }, this.animeDelay);
    }


  }
  
}
</script>

<style lang="scss">
  .gunner {
    &__bg {
      position: relative;
      overflow: hidden;
      background-image: url('sketch-test.png');
      background-size: cover;

      &--blur {
        width: 100%;
        z-index:999;
        // filter: grayscale(1);
        opacity: 0;
      }
      &--blur-2 {
        background-image: url('sketch-test.png');
        background-size: cover;

        position: absolute;
        top: 0;
        width: 100%;
        // height: 600px;
        z-index:1000;
        // filter: grayscale(.3);
        opacity: 0;
      }
      &--lines {
        width: 100%;
        z-index:1001;
        &:after {
          content: '';
          position: absolute;
          top:0px;
          left:0px;
          right:0px;
          bottom:0px;
          z-index:1001;
          background-size:100% 5px;
          opacity:0.3;
          mix-blend-mode: color-burn;
          pointer-events: none;
          width: 100%;
          background: repeating-linear-gradient(0deg, #111 0px, #111 1px, transparent 2px, transparent 5px);
          animation: lines 2s ease-out infinite;
        }
      }
    }
  }
  $animetime: .2s;
  .animaii {
    .gunner {
      &__bg{
        &--blur-2 {
          opacity: 0;
          filter: invert(100%);
          // filter: grayscale(.1);
          // filter: invert(80%);
          animation: invertedMove2 $animetime ease-out 1s 2 ;
        }
        &--blur {
          // filter: invert(100%);
          filter: blur(30);
          filter: grayscale(1);
          opacity: 0;
          animation: invertedMove $animetime ease-out 1s 2 ;
        }
      }
      // &--lines {
      //   display: block;
      // }
    }
  }
@keyframes lines {
  0% {
    background-position:0px 0px;
  }
  100% {
    background-position:0px 25px;
  }
}

@keyframes invertedMove {
  0% {
    opacity: 0;
    transform: translate(0, 0)
  }
  50% {
    opacity: .3;
    transform: translate( -20px, 0px)
  }
  100% {
    opacity: 0;
    transform: translate(0, 0)
  }
}
@keyframes invertedMove2 {
  0% {
    opacity: 0;
    transform: translate( 0px, 0px)
  }
  50% {
    opacity: .3;
    transform: translate(20px, 0)
  }
  100% {
    opacity: 0;
    transform: translate(0, 0)
  }
}

</style>
