<script setup>
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
	width: 750px;
	height: 750px;
	border-radius: 50%;
	filter: blur(200px);
	opacity: 0.75;
	transition: transform 0.2s ease-out;
}
.circle-1 {
	top: -500px;
	right: -700px;
	background: radial-gradient(
		circle at 25% 35%,
		#c85f1f 0%,
		#e87830 25%,
		#a02aae 55%,
		#9f3ddb 100%
	);
	opacity: 0.9;
}

.circle-2 {
	bottom: -500px;
	left: -700px;
	background: radial-gradient(
		circle at 70% 65%,
		#a02aae 0%,
		#7b3cff 30%,
		#1f2a9b 65%,
		#3f5dff 100%
	);
	opacity: 0.9;
}

.bg-circles::before {
	content: "";
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(38,30,48,0.3);
	z-index: -1;
}
</style>
