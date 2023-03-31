<template>
  <div>
    <client-only placeholder="Loading...">
      <Splide :options="{ fixedHeight: 500, rewind: true }">
        <SplideSlide v-for="(image, idx) in imageSet" :key="`sample1-${idx}`">
          <img :src="image" />
        </SplideSlide>
      </Splide>
    </client-only>

    <!--  -->
    <div id="main-slider" class="splide">
      <div class="splide__track">
        <ul class="splide__list">
          <li
            v-for="(image, idx) in imageSet"
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
            v-for="(image, idx) in imageSet"
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
  name: 'SlidejsPage',

  data() {
    return {
      imageSet: [
        'https://picsum.photos/id/15/1680/500',
        'https://picsum.photos/id/16/1680/500',
        'https://picsum.photos/id/17/1680/500',
        'https://picsum.photos/id/18/1680/500',
        'https://picsum.photos/id/19/1680/500',
      ],
    }
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
</style>
