<script setup>
const props = defineProps({
	data: {
		type: Object,
		default: () => ({
			title: 'Default Title',
			subtitle: 'Default Subtitle',
			img: null,
			video: null
		})
	}
});
</script>

<template>
	<section class="title-block container section">
		<div class="title-block__header">
			<h1 class="h1 title-block__title">{{ data.title }}</h1>
			<p class="text-large title-block__subtitle">{{ data.subtitle }}</p>
		</div>
		<div class="title-block__media">
			<img
				:src="data.img"
				v-if="data.img && !data.video"
				class="title-block__media-img"
				loading="lazy"
			>
			<video
				:src="data.video"
				v-if="data.video && !data.img"
				muted
				autoplay
				loop
				class="title-block__media-video"
			></video>

			<button v-if="data.video" class="title-block__media-play">Включить звук</button>
		</div>
	</section>
</template>


<style lang="scss" scoped>
.title-block
{
	display: flex;
	flex-direction: column;
	align-items: center;
	text-align: center;
	gap: 120px;

	@include tablet { gap: 80px; }

	@include mobile { gap: 100px; }

	.title-block__header
	{
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		gap: 40px;

		@include mobile { gap: 35px; }
	}

	.title-block__media
	{
		position: relative;
		max-width: 900px;
		width: 100%;
		height: auto;
		border-radius: 13px;
		overflow: hidden;

		@include tablet { max-width: 550px; }

		@include mobile
		{
			max-width: 100%;
			max-height: 590px;
		}
	}

	.title-block__media-play
	{
		position: absolute;
		top: 15px;
		left: 50%;
		transform: translateX(-50%);
		padding: 14px 24px;
		font-size: 14px;
		font-weight: 300;
		line-height: 150%;
		color: $white;
		background-color: $dark;
		border: none;
		border-radius: 13px;
		outline: none;
		cursor: pointer;
		transition: all 0.3s ease;

		&:hover { background-color: darken($dark, 10%); }
	}
}
</style>