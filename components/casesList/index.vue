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
			<h2 v-if="data.title" class="cases-block__title">{{ data.title }}</h2>
			<p v-if="data.subtitle" class="cases-block__subtitle">{{ data.subtitle }}</p>
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

	.cases-block__header
	{
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 30px;
	}
	.cases-block__title
	{
		font-size: 54px;
		font-weight: 500;
		line-height: 112%;
		text-align: center;
		color: $white;
	}
	.cases-block__subtitle
	{
		max-width: 600px;
		font-size: 18px;
		font-weight: 300;
		line-height: 162%;
		text-align: center;
		color: $disabled;
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