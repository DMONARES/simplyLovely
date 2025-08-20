<script setup>
const props = defineProps({
	link: {
		type: String,
		default: '#',
	},
	isLarge: {
		type: Boolean,
		default: false,
	},
});
</script>

<template>
	<NuxtLink  class="ui-link" :class="{'ui-link--large': isLarge}">
		<slot/>
	</NuxtLink>
</template>

<style lang="scss" scoped>
.ui-link
{
	padding: 11px 20px;
	font-size: 14px;
	font-weight: 300;
	color: $white;
	background-color: transparent;
	border: none;
	border-radius: 13px;
	outline: none;
	transition: all .3s ease;
	cursor: pointer;

	@include text-style(14px);

	&:hover {
		background-color: $greyDark;
	}

	&--large {
		padding: 20px 35px;
		font-size: 27px;
		line-height: 140%;
		font-weight: 300;
		border-radius: 32px;
		color: $greyLight;
		background-color: transparent;

		&:hover {
			color: $white;
			background-color: transparent;
		}

		@media (max-width: 768px)
		{
			font-size: 24px;
		}
	}
}
</style>
