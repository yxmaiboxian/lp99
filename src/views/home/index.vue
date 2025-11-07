<template>
  <div class="home">
    <div v-if="!show" class="btn" @click="changeShow">
      全球热恋
    </div>
    <div v-if="show">
      <div class="box" v-for="(item, index) in imgLength" :key="item" :style="computedStyle(item)">
        <img :style="{ 'animation-duration': computedDuration(item), 'animation-delay': 1 * index + 's' }"
          class="box-img" :src="require(`@/assets/imgs/img (${item}).jpg`)" alt="">
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      imgLength: 100,
      show: false
    }
  },
  computed: {
    computedDuration() {
      return (item) => {
        let flag = Math.random()
        let num = 0.5
        if (flag > 0.3) {
          num = flag * 5
        }
        return num + 's'
      }

    },
    computedStyle() {
      return (item) => {
        let left = `${Math.floor(Math.random() * 101)}`
        let top = `${Math.floor(Math.random() * 101)}`
        return {
          left: `${left}%`,
          top: `${top}%`,
          transform: `translate(-${left}%, -${top}%)`
        }
      }

    }
  },
  methods: {
    changeShow() {
      this.show = true
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  @keyframes myAnimation {
    0% {
      /* 起始状态 */
      transform: scale(.05);
    }

    75% {
      opacity: 0.9
    }

    100% {
      /* 结束状态 */
      transform: scale(1) translateZ(500px);
      opacity: 1
    }
  }

  width: 100%;
  height: 100vh;
  overflow: hidden;

  .box {
    position: fixed;
    transform-style: preserve-3d;
    width: 240px;

    &-img {
      opacity: 0;
      width: 100%;
      animation: myAnimation 1s forwards;
    }
  }

  .btn {
    width: 240px;
    height: 100px;
    line-height: 80px;
    font-size: 30px;
    text-align: center;
    color: pink;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    border-radius: 20px;
    cursor: pointer;
    overflow: hidden;

    &::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      color: black;
      width: 100%;
      height: 100%;
      background: linear-gradient(rgba(255, 255, 255, 0.4), rgba(255, 255, 255, 0.4)), url('@/assets/imgs/img (7).jpg');
      background-repeat: no-repeat;
      filter: blur(1px);
      background-position: center center;
      background-size: cover;

    }

    &::after {
      content: '全球热恋';
      position: absolute;
      font-size: 40px;
      left: 50%;
      top: 50%;
      white-space: nowrap;
      transform: translate(-50%, -50%);
    }
  }
}
</style>