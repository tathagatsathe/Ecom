<template>
<div>
    <transition-group name='fade' tag='div'>
      <div v-for="i in [currentIndex]" :key='i'>
        <img :src="currentImg" />
      </div>
    </transition-group>
    <a class="prev" @click="prev" href='#'>&#10094;</a>
  <a class="next" @click="next" href='#'>&#10095;</a>
  </div>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      images: [
        "https://i.gadgets360cdn.com/large/flipkartgrandgadgetssale_main_1566890393492.jpg",
        "https://images.freekaamaal.com/post_images/1578392330.png",
        "https://piunikaweb.com/wp-content/uploads/2019/08/oneplus_7_pro_5g_experience_the_power_of_5g_banner-750x354.jpg",
        "https://i.ytimg.com/vi/3-1A_NEATfU/maxresdefault.jpg"      ],
      timer: null,
      currentIndex: 0
    };
  },

  mounted: function() {
    this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 4000);
    },

    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  }
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.1s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width:50%;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width:50%;
  opacity: 0;
}

img {
  height:500px;
  width:30%
}

.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  /* font-size: 18px; */
  transition: 0.1s ease;
  /* border-radius: 0 4px 4px 0; */
  text-decoration: none;
  user-select: none;
}

.next {
  right: 0;
}

.prev {
  left: 0;
}

.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.9);
}
</style>