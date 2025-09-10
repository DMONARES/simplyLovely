<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';

const props = defineProps({
  cases: {
    type: Array,
    required: true,
    default: () => []
  },
	lastCardText: {
    type: String,
    default: 'Смотреть больше кейсов'
  },
	cardMedium: {
		type: Boolean,
		default: false
	},
});

const swiperOptions = {
  slidesPerView: 1,
  spaceBetween: 30,
  breakpoints: {
    640: {
      slidesPerView: 2,
    },
    1024: {
      slidesPerView: 3,
    },
  }
};
</script>

<template>
  <ClientOnly>
    <Swiper
      class="case-slider"
      :slides-per-view="swiperOptions.slidesPerView"
      :space-between="swiperOptions.spaceBetween"
      :breakpoints="swiperOptions.breakpoints"
    >
      <SwiperSlide v-for="card in cases" :key="card.id || card.title" class="case-slider__item">
        <CasePartsCard :card="card" :black-text="card.blackText" :cardMedium="cardMedium" />
      </SwiperSlide>
      <SwiperSlide class="case-slider__item">
        <CasePartsLastCard :cardMedium="cardMedium">{{ lastCardText }}</CasePartsLastCard>
      </SwiperSlide>
    </Swiper>
  </ClientOnly>
</template>

<style lang="scss" scoped>
.case-slider {
	overflow: visible;
  width: 100%;
  height: 100%;

	.case-slider__item {
		max-width: 350px;
	}
}
</style>