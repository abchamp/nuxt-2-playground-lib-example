<template>
  <div id="glidejsExample" class="glide">
    <div class="glide__track" data-glide-el="track">
      <ul class="glide__slides">
        <li v-for="(image, idx) in images" :key="idx" class="glide__slide">
          <img :src="image" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Glide from '@glidejs/glide'

export default {
  name: 'GlidejsExample',
  props: {
    images: {
      type: Array,
      default: () => [],
    },
  },
  data: () => ({
    glide: null,
  }),
  mounted() {
    this.$nextTick(() => {
      this.glideInit()
    })
  },
  methods: {
    glideInit() {
      if (this.glide !== null) {
        this.glideDestory()
      }

      this.glide = new Glide('#glidejsExample', {
        type: 'carousel',
        startAt: 0,
        perView: 3,
      })
      this.glide.mount()
    },

    glideDestroy() {
      this.glide.destroy()
      this.glide = null
    },
  },
}
</script>
