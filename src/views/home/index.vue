<template>
  <div class="home">
    <div class="box" v-for="(item) in imgLength" :key="item"
      :style="{ left: `${Math.floor(Math.random() * 101)}vw`, top: `${Math.floor(Math.random() * 101)}vh` }">
      <img :style="{ 'animation-duration': computedDuration(item) }" class="box-img"
        :src="require(`@/assets/imgs/img (${item}).jpg`)" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      imgLength: 35
    }
  },
  computed: {
    computedDuration() {
      return (item) => {
        let flag = Math.random()
        let num = 2
        if (flag > 0.3) {
          num = flag * 10
        }
        return num + 's'
      }

    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  @keyframes myAnimation {
    0% {
      /* 起始状态 */
      transform: scale(.2);
      opacity: 1
    }

    50% {
      /* 中间状态 */
      transform: scale(2.5) translateZ(500px);
      opacity: 0.8
    }
    80% {
      opacity: 0.7
    }
    100% {
      /* 结束状态 */
      transform: scale(1);
      opacity: 0
    }
  }

  width: 100vw;
  height: 100vh;
  position: relative;
  overflow: hidden;
  transform-style:preserve-3d;

  .box {
    position: absolute;

    &-img {
      width: 80px;
      animation: myAnimation 1s infinite;
      ;
    }
  }
}
</style>