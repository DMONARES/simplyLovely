<script setup>
const props = defineProps({
	link: {
		type: String,
		default: '#',
	},
});
</script>

<template>
	<NuxtLink  class="ui-link">
		<slot/>
	</NuxtLink>
</template>

<style lang="scss" scoped>
.ui-link
{
	padding: 11px 20px;
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
}
</style>
