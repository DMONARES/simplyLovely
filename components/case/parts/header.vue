<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
    default: () => ({})
  },
  variant: {
    type: String,
    default: 'column'
  }
});
</script>

<template>
  <div class="case-header" :class="`case-header--${variant}`">
    <!-- Вариант 1: Колонка -->
    <div v-if="variant === 'column'" class="case-header__column">
      <h2 class="h2 case-header__title">{{ data.title }}</h2>
      <p v-if="data.subtitle" class="p-text case-header__subtitle">{{ data.subtitle }}</p>
    </div>

    <!-- Вариант 2: Ряд -->
    <div v-else-if="variant === 'row'" class="case-header__row">
      <h2 class="h2 case-header__title">{{ data.title }}</h2>
      <p v-if="data.subtitle" class="p-text case-header__subtitle">{{ data.subtitle }}</p>
    </div>

    <!-- Вариант 3: Ряд с навигацией -->
    <!-- <div v-else-if="variant === 'row-with-nav'" class="case-header__row-with-nav">
      <div class="case-header__text">
        <h2 class="h2 case-header__title">{{ data.title }}</h2>
        <p v-if="data.subtitle" class="p-text case-header__subtitle">{{ data.subtitle }}</p>
      </div>
      <div class="case-header__nav">
        <slot name="navigation"></slot>
      </div>
    </div> -->

  </div>
</template>

<style lang="scss" scoped>
	.case-header
	{
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 30px;

		@include tablet { gap: 55px; }

		@include mobile { gap: 25px; }

		&--row
		{
			display: grid;
			grid-template-columns: repeat(2, 1fr);

			@include mobile
			{
				grid-template-columns: repeat(1, 1fr);
				gap: 56px;
			}
		}
	}
</style>