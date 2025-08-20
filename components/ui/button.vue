<script setup></script>

<template>
	<div class="ui-button">
		<slot/>
	</div>
</template>

<style lang="scss" scoped>
.ui-button
{
	position: relative;
	max-width: max-content;
	padding: 10px 20px;
	font-size: 16px;
	font-weight: 300;
	line-height: 140%;
	color: $white;
	background-color: transparent;
	border: 1px solid $white;
	border-radius: 13px;
	transition: all .2s ease;
	overflow: hidden;
	cursor: pointer;

	&::after
	{
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		transform: scaleX(0);
		transform-origin: right;
		background-color: $white;
		transition: transform 0.3s;
		z-index: -1;
	}

	&:hover
	{
		color: $dark;
		&::after
		{
			transform: scaleX(1);
			transform-origin: left;
		}
		// background-color: $white;
	}
}
</style>
