<script setup>
import { onMounted, onBeforeUnmount } from "vue";

let handleScroll;

onMounted(() => {
	const circle1 = document.querySelector(".circle-1");
	const circle2 = document.querySelector(".circle-2");

	handleScroll = () => {
		const scrollY = window.scrollY;

		// Движение только по вертикали
		circle1.style.transform = `translateY(${scrollY * 0.3}px)`;
		circle2.style.transform = `translateY(${-scrollY * 0.3}px)`;
	};

	window.addEventListener("scroll", handleScroll);
});

onBeforeUnmount(() => {
	window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
	<div class="bg-circles">
		<div class="circle circle-1"></div>
		<div class="circle circle-2"></div>
	</div>
</template>

<style scoped>
.bg-circles {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	overflow: hidden;
	z-index: 0;
	pointer-events: none;
}

.circle {
	position: absolute;
	width: 900px;
	height: 900px;
	border-radius: 50%;
	filter: blur(150px);
	opacity: 0.75;
	transition: transform 0.2s ease-out;
}

.circle-1 {
	top: -300px;
	right: -700px;
	background: radial-gradient(
		circle at 25% 35%,
		#e77726 0%,
		#ff9a4d 25%,
		#cb3ace 55%,
		#d66ee8 100%
	);
}

.circle-2 {
	bottom: -300px;
	left: -600px;
	background: radial-gradient(
		circle at 70% 65%,
		#cb3ace 0%,
		#9a5bff 30%,
		#2947e8 65%,
		#4a74ff 100%
	);
}
</style>
