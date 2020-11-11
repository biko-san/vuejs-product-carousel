<template>
  <div class="container">
    <!-- add the carousel to your page -->
    <carousel :products="exampleProducts" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Carousel from '~/components/Carousel.vue'

export default Vue.extend({
  components: { Carousel },
  data() {
    return {
      // replace example products with a products array[] from your API
      exampleProducts: [
        {
          name: 'example product',
          price: '345',
          image: 'https://images.unsplash.com/photo-1517694712202-14dd9538aa97',
        },
        {
          name: 'example product',
          price: '345',
          image: 'https://images.unsplash.com/photo-1517694712202-14dd9538aa97',
        },
      ],
    }
  },
})
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
