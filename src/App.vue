<template>
  <div>
    <div class="stars">
      <div class="start">
        <a href="www.baidu.com">
          <svg class="icon">
            <use xlink:href="#icon-icon-test" />
          </svg>
        </a>
      </div>
      <div v-for="(item,index) in starsCount" :key="index" class="star" ref="star"></div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      starsCount: 800,
      distance: 800
    };
  },
  mounted() {
    let _this = this;
    let starArray = _this.$refs.star;
    console.log(starArray);
    starArray.forEach(item => {
      var speed = 0.2 + Math.random() * 1;
      var thisDistance = _this.distance + Math.random() * 300;
      item.style.transformOrigin = `0 0 ${thisDistance}px`;
      item.style.transform = `translate3d(0,0,-${thisDistance}px) rotateY(${Math.random() *
        360}deg) rotateX(${Math.random() * -50}deg) scale(${speed},${speed})`;
    });
  }
};
</script>
<style>
@keyframes rotate {
  0% {
    transform: perspective(400px) rotateZ(20deg) rotateX(-400deg) rotateY(0);
  }

  100% {
    transform: perspective(400px) rotateZ(20deg) rotateX(-400deg)
      rotateY(-360deg);
  }
}

.stars {
  transform: perspective(500px);
  transform-style: preserve-3d;
  position: absolute;
  perspective-origin: 50% 100%;
  left: 50%;
  animation: rotate 90s infinite linear;
  bottom: 0;
}

.star {
  width: 4px;
  height: 4px;
  background: #f7f7b8;
  position: absolute;
  top: 0;
  left: 0;
  backface-visibility: hidden;
}
.start {
  position: absolute;
  bottom: 150px;
}
</style>
