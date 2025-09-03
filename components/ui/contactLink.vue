<script setup>
import { ref } from "vue";

const props = defineProps({
	link: {
		type: String,
		default: "#",
	},
	tabs: {
		type: Array,
		default: () => [],
	},
	light: {
		type: Boolean,
		default: false,
	},
	inline: {
		type: Boolean,
		default: false,
	},
});

const activeIndex = ref(0);

const activeValue = computed(() => {
	if (props.tabs.length > 0) {
		return props.tabs[activeIndex.value].value;
	}
	return null;
});

function selectTab(index) {
	activeIndex.value = index;
}
</script>

<template>
	<div class="contact-link" :class="{'contact-link--inline': inline}">
		<div class="contact-link__base">
			<NuxtLink :href="link" class="contact-link__text" :class="{'contact-link__text--light': light, 'contact-link__text--large': inline}">
				<slot v-if="!tabs.length" />
				<span v-else>{{ activeValue }}</span>
			</NuxtLink>
		</div>

		<div v-if="tabs.length" class="contact-link__tabs" :class="{'contact-link__tabs--large': inline}">
			<button
				v-for="(tab, index) in tabs"
				:key="index"
				@click="selectTab(index)"
				:class="{ active: index === activeIndex }"
			>
				{{ tab.label }}
			</button>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.contact-link
{
	max-width: max-content;
	display: flex;
	flex-direction: column;
	gap: 20px;

	&--inline
	{
		flex-direction: row-reverse;
		align-items: center;
		gap: 30px;
	}

	&__base
	{
		display: flex;
		align-items: center;
		gap: 14px;
	}

	&__text
	{
		font-size: 15px;
		font-weight: 300;
		color: $greyLight;
		transition: all .3s ease;

		&:hover
		{
			color: $white;
		}

		&--light { color: $white; }

		&--large { font-size: 16px; }
	}

	&__tabs
	{
		display: flex;
		align-items: center;
		gap: 10px;

		button
		{
			font-size: 12px;
			font-weight: 300;
			color: $greyLight;
			transition: all .3s ease;

			&.active { color: $white; }
		}
	}

	&__tabs--large
	{
		gap: 30px;

		button { font-size: 16px; }
	}
}
</style>
