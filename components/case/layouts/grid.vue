<script setup>
import { useWindowSize } from '@vueuse/core';

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
  showLastCard: {
    type: Boolean,
    default: true
  },
	cardMedium: {
		type: Boolean,
		default: false
	},
});

const { width: windowWidth } = useWindowSize();

const displayedItems = computed(() => {
  return windowWidth.value <= 675 ? props.cases.slice(0, 4) : props.cases;
});
</script>

<template>
  <ul class="cases-grid">
    <li v-for="(card, i) in displayedItems" :key="card.title" class="cases-grid__item">
      <CasePartsCard :card="card" :black-text="card.blackText" :cardMedium="cardMedium" />
    </li>
    <li v-if="showLastCard" class="cases-grid__item">
      <CasePartsLastCard :cardMedium="cardMedium">{{ lastCardText }}</CasePartsLastCard>
    </li>
  </ul>
</template>

<style lang="scss" scoped>

</style>