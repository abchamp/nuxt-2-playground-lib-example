<template>
  <div>
    <div id="main-slider" class="splide">
      <div class="splide__track">
        <ul class="splide__list">
          <li
            v-for="(image, idx) in images"
            :key="`sample2-thumbnails-${idx}`"
            class="splide__slide"
          >
            <img :src="image" />
          </li>
        </ul>
      </div>
    </div>
    <div id="thumbnail-slider" class="splide">
      <div class="splide__track">
        <ul class="splide__list">
          <li
            v-for="(image, idx) in images"
            :key="`sample2-thumbnails-${idx}`"
            class="splide__slide"
          >
            <img :src="image" />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Splide from '@splidejs/splide'

export default {
  name: 'SlidejsSampleExample',
  props: {
    images: {
      type: Array,
      default: () => [],
    },
  },
  mounted() {
    this.$nextTick(() => {
      this.syncMainAndThumbnail()
    })
  },
  methods: {
    syncMainAndThumbnail() {
      const thumbnailEle = document.querySelector('#thumbnail-slider')
      const mainEle = document.querySelector('#main-slider')
      if (thumbnailEle !== null && mainEle !== null) {
        const mainslider = new Splide('#main-slider', {
          type: 'fade',
          rewind: true,
          pagination: false,
          arrows: false,
        })
        const thumbnailslider = new Splide('#thumbnail-slider', {
          fixedWidth: 100,
          fixedHeight: 60,
          gap: 10,
          rewind: true,
          pagination: false,
          cover: true,
          isNavigation: true,
          breakpoints: {
            600: {
              fixedWidth: 60,
              fixedHeight: 44,
            },
          },
        })

        mainslider.sync(thumbnailslider)
        mainslider.mount()
        thumbnailslider.mount()
      }
    },
  },
}
</script>

<style scoped>
.splide__slide img {
  width: 100%;
  height: auto;
}
.splide__slide {
  opacity: 0.3;
}

.splide__slide.is-active {
  opacity: 1;
}
</style>
