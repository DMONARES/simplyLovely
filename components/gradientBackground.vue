<script setup>
import { onMounted, onBeforeUnmount } from "vue";

let handleScroll;

onMounted(() => {
	const circles = document.querySelectorAll(".circle");

	handleScroll = () => {
		const scrollY = window.scrollY;
		circles[0].style.transform = `translate(${scrollY * 0.1}px, ${
			scrollY * 0.2
		}px)`;
		circles[1].style.transform = `translate(${-scrollY * 0.1}px, ${
			scrollY * 0.15
		}px)`;
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
}

.circle {
	position: absolute;
	width: 900px;
	height: 900px;
	border-radius: 50%;
	filter: blur(150px);
	opacity: 0.7;
	animation: float 12s ease-in-out infinite alternate;
}

.circle-1 {
	top: -400px;
	left: -400px;
	background: radial-gradient(circle at 30% 30%, #e77726, #cb3ace);
}

.circle-2 {
	bottom: -400px;
	right: -400px;
	background: radial-gradient(circle at 70% 70%, #cb3ace, #2947e8);
}

@keyframes float {
	0% {
		transform: translate(0, 0) scale(1);
	}
	100% {
		transform: translate(20px, -20px) scale(1.05);
	}
}
</style>
