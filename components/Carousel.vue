<template>
  <div class="carousel-container relative m-4 flex flex-col">
    <div class="grid grid-cols-2 m-4 justify-items-center items-center">
      <div
        v-for="product in currentProducts"
        :key="product.id"
        class="p-2 flex flex-wrap place-items-stretch"
      >
        <img :src="product.image" alt="" />
        <p class="text-base">{{ product.name }}</p>
        <p>
          ksh.
          {{
            product.price.toFixed().replace(/(\d)(?=(\d{3})+(?!\d))/g, '$1,')
          }}
        </p>
        <button class="border-2 rounded px-4 py-2 m-1 font-light">
          Add To Cart
        </button>
      </div>
    </div>

    <div class="flex flex-row justify-center space-x-2">
      <div v-for="(n, index) in slides" :key="index" class="">
        <div
          class="rounded-full h-4 w-4 bg-gray-400 hover:bg-gray-900"
          @click="goToSlide(n)"
        ></div>
      </div>
    </div>

    <font-awesome-icon
      :icon="['fa', 'chevron-left']"
      v-if="slidePosition > 1"
      class="carousel-button carousel-button--left"
      @click="goToPreviousSlide"
    />
    <font-awesome-icon
      :icon="['fa', 'chevron-right']"
      v-if="slidePosition < slidesNumber"
      class="carousel-button carousel-button--right"
      @click="goToNextSlide"
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import products from '~/data/products'

export default Vue.extend({
  props: {
    products: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      slidePosition: 1,
      slidesLimit: 5,
      slides: [1, 2, 3, 4, 5],
    }
  },
  computed: {
    slidesNumber() {
      return Math.floor(this.products.length / 2)
    },
    currentProducts() {
      let firstProduct = this.slidePosition * 2 - 2
      let secondProduct = this.slidePosition * 2 - 1
      return [this.products[firstProduct], this.products[secondProduct]]
    },
  },
  mounted() {},

  methods: {
    goToSlide(slideKey) {
      this.slidePosition = slideKey
    },
    goToNextSlide() {
      if (this.slidePosition % this.slidesLimit === 0) {
        console.log(`get the next slice`)
        this.slides = this.slides.reduce(
          (accumulator, item) => [...accumulator, item + 5],
          []
        )
      }
      this.slidePosition += 1
    },
    goToPreviousSlide() {
      if (this.slidePosition % this.slidesLimit === 1) {
        this.slides = this.slides.reduce(
          (accumulator, item) => [...accumulator, item - 5],
          []
        )
      }
      this.slidePosition -= 1
    },
  },
})
</script>

<style scoped lang="scss">
.carousel-button {
  position: absolute;
  bottom: 50%;
  transform: translateY(-50%);
  @apply text-2xl;
}

.carousel-button--left {
  left: 0;
}
.carousel-button--right {
  right: 0;
}
</style>
