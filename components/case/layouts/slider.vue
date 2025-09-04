<script setup>
const props = defineProps({
  cases: {
    type: Array,
    required: true,
    default: () => []
  }
});

</script>

<template>
  <div class="case-slider">
    <div class="swiper-wrapper">
      <div v-for="card in cases" :key="card.title" class="swiper-slide">
        <CasePartsCard :card="card" :black-text="card.blackText" />
      </div>
			<CasePartsLastCard/>
    </div>
  </div>
</template>

<style lang="scss" scoped>

</style>