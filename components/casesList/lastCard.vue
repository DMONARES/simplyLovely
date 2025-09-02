<script setup>

</script>

<template>
	<nuxt-link to="/" class="last-card">
		<p>Смотреть больше кейсов</p>
		<img src="/img/cases/lastBlogGif.gif" loop="loop" playsinline loading="lazy" class="last-card__bg">
		<div class="last-card__dark"></div>
	</nuxt-link>
</template>

<style lang="scss" scoped>
.last-card
{
	padding: 50px;
  width: 100%;
  aspect-ratio: 3/4;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
  overflow: hidden;

	p
	{
		font-size: 26px;
		font-weight: 300;
		line-height: 130%;
		text-align: center;
		color: $white;
		z-index: 20;
	}

	.last-card__bg
	{
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		border-radius: 30px;
		z-index: 1;
	}

	.last-card__dark
	{
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.5);
		border-radius: 30px;
		overflow: hidden;
		transition: all .3s ease;
		z-index: 2;
	}

	&:hover
	{
		.last-card__dark
		{
			opacity: 0;
		}
	}
}
</style>