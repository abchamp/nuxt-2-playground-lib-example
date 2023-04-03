<template>
  <GlidejsExample :images="images" />
</template>

<script>
export default {
  name: 'GlidejsPage',
  data: () => ({
    images: [
      'https://picsum.photos/id/15/1680/500',
      'https://picsum.photos/id/16/1680/500',
      'https://picsum.photos/id/17/1680/500',
      'https://picsum.photos/id/18/1680/500',
      'https://picsum.photos/id/19/1680/500',
    ],
  }),
}
</script>
