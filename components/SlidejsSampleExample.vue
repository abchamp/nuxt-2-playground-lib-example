<template>
  <client-only placeholder="Loading...">
    <Splide :options="{ fixedHeight: 500, rewind: true }">
      <SplideSlide v-for="(image, idx) in images" :key="`sample1-${idx}`">
        <img :src="image" />
      </SplideSlide>
    </Splide>
  </client-only>
</template>

<script>
export default {
  name: 'SlidejsSampleExample',
  props: {
    images: {
      type: Array,
      default: () => [],
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
