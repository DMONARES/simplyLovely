<script setup>
const dradientDots = ref(["img/gradient_dot.png", "img/gradient_dot.png"])
const gradient = ref([])

const setDotsStyle = (styles) => gradient.value.forEach(el => Object.assign(el.style, styles))

const handleScroll = () => {
  setDotsStyle({
    transition: "2.5s .7s opacity, 1.1s transform ease",
    transform: `rotate(${window.scrollY / 20}deg)`
  })
}

const dotsStop = () => {
  setDotsStyle({
    transition: "2.5s .7s opacity, .9s transform ease",
    transform: `translateY(0) rotate(${window.scrollY / 20}deg)`
  })
}

onMounted(() => {
  window.addEventListener("scroll", handleScroll)
  document.onscrollend = dotsStop
  nextTick(() => setDotsStyle({ opacity: 1 }))
})

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll)
  document.onscrollend = null
})
</script>

<template>
  <div class="default-layout">
    <div class="background-gradient">
      <img
        v-for="(item, i) in dradientDots"
        :key="i"
        :src="item"
        :ref="(el) => gradient[i] = el"
        loading="lazy"
      />
    </div>
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

.background-gradient {
	width: 100%;
	height: 100vh;
	position: fixed;
	display: flex;
	align-items: center;
	justify-content: space-between;
	pointer-events: none;
	z-index: 0;

	img {
		user-select: none;
		opacity: 0;
		transition: 2.5s 0.7s opacity, 0.7s transform ease;
		width: 150vw;
		position: absolute;

		&:first-child {
			left: -65%;
		}

		&:last-child {
			right: -65%;
		}

		@media screen and (max-width: 1100px) {
			height: 220vw;
			width: 220vw;

			&:first-child {
				left: -140%;
			}
			&:last-child {
				right: -140%;
			}
		}
	}
}
</style>
