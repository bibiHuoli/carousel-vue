<script>
  export default {
    name: 'Carousel',
    data() {
      return {
        currentIndex: 0,
      }
    },
    // mutations: {
    //   nextIndex: () => {
    //     if(this.currentIndex < this.slider.length - 1) {
    //       this.currentIndex ++;
    //     }
    //   },
    //   prevIndex: () => {
    //     if(this.currentIndex > 0) {
    //       this.currentIndex --;
    //     }
    //   },
    // },
  }
</script>

<template>
  <div class="carousel">
    <div class="slider">
      <div class="slide">
        <img src="https://picsum.photos/300" />
      </div>
      <div class="slide">
        <img src="https://picsum.photos/300/400" />
      </div>
      <div class="slide">
        <img src="https://picsum.photos/400/300" />
      </div>
    </div>
    <div class="nav">
      <button class="indicator" @click=""></button>
      <button class="indicator" @click=""></button>
      <button class="indicator" @click=""></button>
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
    background: #a0a;
    height: 500px;
    width: 400px;
  }
  .slider {
    background: #00a;
    color: #ddd;
    height: 400px;
  }
  .slide {
    height: 100%;
    width: 100%;
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
