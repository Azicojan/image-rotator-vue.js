
<template>
  <div>
    <img v-show-image :src='currentImage'>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        'https://picsum.photos/id/103/500/500',
        'https://picsum.photos/id/110/500/500',
        'https://picsum.photos/id/106/500/500'
      ],
      index: 0,
      intervalId: null
    }
  },
  computed: {
    currentImage() {
      return this.images[this.index];
    }
  },
  directives: {
    'show-image': {
      inserted: function (el, binding) {
        el.src = binding.value;
      }
    }
  },
  created() {
    this.intervalId = setInterval(() => {
      const randomIndex = Math.floor(Math.random() * this.images.length);
      this.index = randomIndex;
    }, 2000);
  },
  destroyed() {
    clearInterval(this.intervalId);
  }
}
</script>



