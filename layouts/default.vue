<script setup></script>

<template>
	<div class="default-layout">
		<GradientBackground />
		<div class="layout-content">
			<Header />
			<main>
				<slot />
			</main>
			<Footer />
		</div>
	</div>
</template>

<style lang="scss">
.layout-content {
	position: relative;
	z-index: 1;
}
</style>
