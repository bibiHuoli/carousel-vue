<script>
  export default {
    name: 'Carousel',
    data() {
      return {
        currentIndex: 0,
        images: [
          'https://picsum.photos/300',
          'https://picsum.photos/300/400',
          'https://picsum.photos/400/300',
        ],
        touch: {
          startX: 0,
          endX: 0,
        },
      }
    },
    computed: {
      sliderLength() {
        return {
          width: `${this.images.length * 100}%`,
        }
      },
      slidePosition() {
        return {
          transform: `translateX(${this.currentIndex * - 100}%)`,
        }
      },
    },
    methods: {
      nextIndex() {
        if(this.currentIndex < this.images.length - 1) {
          this.currentIndex ++;
          // console.log(this.currentIndex);
        }
      },
      prevIndex() {
        if(this.currentIndex > 0) {
          this.currentIndex --;
          // console.log(this.currentIndex);
        }
      },
      touchStart(event) {
        this.touch.startX = event.touches[0].clientX;
        this.touch.endX = 0;
      },
      touchMove(event) {
        this.touch.endX = event.touches[0].clientX;
      },
      touchEnd() {
        if(!this.touch.endX) return;
        if(Math.abs(this.touch.endX - this.touch.startX) < 20) return;
        if(this.touch.endX < this.touch.startX) {
          return this.nextIndex();
        } else {
          return this.prevIndex();
        };
      },
    },
    mounted() {
      this.$el.addEventListener('touchstart', this.touchStart);
      this.$el.addEventListener('touchmove', this.touchMove);
      this.$el.addEventListener('touchend', this.touchEnd);
    },
  }
</script>

<template>
  <div class="carousel">
    <div class="slider" :style="sliderLength" >
      <div
        class="slide"
        :key="index"
        :style="slidePosition"
        v-for="image in images"
      >
        <img :src="image" />
      </div>
    </div>
    <div class="nav">
      <div :key="index" v-for="image in images">
        <button class="indicator"></button>
      </div>
    </div>
  </div>
</template>

<style scoped>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  .carousel {
    height: 500px;
    overflow: hidden;
    width: 400px;
  }
  .slider {
    color: #ddd;
    display: flex;
    flex-direction: row;
    height: 400px;
  }
  .slide {
    height: 100%;
    width: 100%;
    transition: transform 200ms ease-in-out;
  }
  .slide img {
    height: 100%;
    object-fit: cover;
    object-position: center;
    width: 100%;
  }
  .nav {
    display: flex;
    flex-direction: row;
    gap: 2rem;
    margin-top: 2rem;
    place-content: center;
  }
  .nav .indicator {
    background-color: #fff4;
    border: none;
    border-radius: 50%;
    cursor: pointer;
    height: 3rem;
    width: 3rem;
  }
  .nav .indicator:focus {
    outline: none;
  }
</style>
