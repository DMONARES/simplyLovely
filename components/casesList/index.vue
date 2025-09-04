<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
    default: () => ({})
  },
});

const windowWidth = ref(0);

const updateWidth = () => {
  if (typeof window !== 'undefined') {
    windowWidth.value = window.innerWidth;
  }
};

onMounted(() => {
  updateWidth();
  window.addEventListener("resize", updateWidth);
});

onUnmounted(() => {
  if (typeof window !== 'undefined') {
    window.removeEventListener("resize", updateWidth);
  }
});
</script>


<template>
	<section class="cases-block container section">
		<div class="cases-block__header" v-if="data.title || data.subtitle">
			<h2 v-if="data.title" class="h2 cases-block__title">{{ data.title }}</h2>
			<p v-if="data.subtitle" class="p-text cases-block__subtitle">{{ data.subtitle }}</p>
		</div>
		<ul class="cases-block__list">
			<CasesListCard
				v-for="(card, i) in (windowWidth <= 675 ? data.cases.slice(0, 4) : data.cases)"
				:key="card.title"
				:card="card"
				:blackText="card.blackText"
				class="cases-block__card"
			/>
			<CasesListLastCard/>
		</ul>
	</section>
</template>

<style lang="scss" scoped>
.cases-block
{
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 95px;

	@include tablet { gap: 80px; }

	@include mobile { gap: 40px; }

	.cases-block__header
	{
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 30px;

		@include tablet { gap: 55px; }

		@include mobile { gap: 25px; }
	}

	.cases-block__list
	{
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 30px;

		@media (max-width: 1600px) { grid-template-columns: repeat(3, 1fr); }

		@media (max-width: 1024px) { grid-template-columns: repeat(2, 1fr); }

		@media (max-width: 675px) { grid-template-columns: 1fr; }
	}
}
</style>