<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
    default: () => ({})
  },
});
</script>

<template>
	<div class="banner container section">
		<div class="banner__wrapper">
			<ul class="banner__list">
				<li v-for="item in data.bannerItems" :key="item.subtitle" class="banner__item">
					<div class="banner__item-header">
						<h2 class="banner__item-title">{{ item.title }}</h2>
						<div class="banner__item-subtitle">{{ item.subtitle }}</div>
					</div>
					<span class="banner__item-divider"></span>
					<p class="banner__item-description">{{ item.description }}</p>
				</li>
			</ul>
			<nuxt-link to="/" class="banner__link"></nuxt-link>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.banner
{

	.banner__wrapper
	{
		position: relative;

		&::after
		{
			content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      height: 110%;
      width: 80%;
      transform: translate(-50%, -50%);
      background: linear-gradient(to left, rgba(97, 12, 236, .5), rgba(219, 0, 255, .5));
      filter: blur(50px);
      border-radius: 30px;
      z-index: -1;
      opacity: 0.8;
		}
	}
	.banner__list
	{
		padding: 80px 70px;
		background-color: $darkBg;
		border-radius: 30px;
		display: flex;
		align-items: center;
		gap: 70px;
	}
	.banner__item
	{
		display: flex;
		flex-direction: column;
		gap: 30px;
	}
	.banner__item-header
	{
		color: $white;
	}
	.banner__item-title
	{
		font-size: 64px;
		font-weight: 500;
		line-height: 126%;
	}
	.banner__item-subtitle
	{
		font-size: 26px;
		font-weight: 300;
		line-height: 130%;
	}
	.banner__item-divider
	{
		width: 100%;
		height: 1px;

		&:nth-child(1) { background: linear-gradient(90deg, #00f0ff, #ff00b5 355%); }
		&:nth-child(2) { background: linear-gradient(90deg, #00f0ff -127.33%, #ff00b5 225.33%); }
		&:nth-child(3) { background: linear-gradient(90deg, #00f0ff -254.33%, #ff00b5 100.08%); }
	}
	.banner__item-description
	{
		font-size: 16px;
		font-weight: 300;
		line-height: 150%;
		color:$disabled;
	}
}
</style>