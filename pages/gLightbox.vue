<template>
  <div>
    <p>Click on Image</p>
    <img
      v-for="(image, idx) in images"
      :key="idx"
      :src="image"
      @click="openGLightBox"
    />
  </div>
</template>

<script>
import GLightbox from 'glightbox'

export default {
  name: 'GLightboxPage',
  data: () => ({
    images: [
      'https://picsum.photos/id/15/150/150',
      'https://picsum.photos/id/16/150/150',
      'https://picsum.photos/id/17/150/150',
      'https://picsum.photos/id/18/150/150',
      'https://picsum.photos/id/19/150/150',
    ],
  }),
  methods: {
    openGLightBox() {
      const boxImage = []
      for (let i = 0; i < this.images.length; i++) {
        boxImage.push({
          href: this.images[i],
          type: 'image',
        })
      }

      if (boxImage.length > 0) {
        const myGallery = GLightbox({ startAt: 0, elements: boxImage })
        myGallery.open()
      }
    },
  },
}
</script>
