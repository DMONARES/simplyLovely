<script setup>
import { ref, onMounted, onBeforeUnmount, resolveComponent } from "vue";

const navLinks = [
	{ link: "#", text: "Кейсы" },
	{ link: "#", text: "Услуги" },
	{ link: "#", text: "Агенство" },
	{ link: "#", text: "Блог" },
	{ link: "#", text: "Вакансии" },
	{ link: "#", text: "Контакты" },
];

const contactLinks = [
	{
		icon: resolveComponent("IconsPhone"),
		link: "#",
		tabs: [
			{ label: "Москва", value: "Позвонить +7-(999)-999-99-99" },
			{ label: "Санкт-Петербург", value: "Позвонить +7-(888)-888-88-88" },
		],
		light: true,
	},
	{
		icon: resolveComponent("IconsMessage"),
		link: "#",
		text: "Отправить заявку",
	},
	{ icon: resolveComponent("IconsTg"), link: "#", text: "Написать в Telegram" },
	{
		icon: resolveComponent("IconsWhatsapp"),
		link: "#",
		text: "Написать в WhatsApp",
	},
];

const showNav = ref(true);
const burgerStage = ref("");

const handleScroll = () => {
	showNav.value = window.scrollY === 0;
};

const toggleMenu = () => {
	if (burgerStage.value === "") {
		burgerStage.value = "merge";
		setTimeout(() => {
			burgerStage.value = "active";
		}, 150);
	} else {
		burgerStage.value = "merge";
		setTimeout(() => {
			burgerStage.value = "";
		}, 150);
	}
};

onMounted(() => {
	window.addEventListener("scroll", handleScroll);
	handleScroll();
});

onBeforeUnmount(() => {
	window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
	<header class="header">
		<div class="header__container">
			<nuxt-link to="/" class="header__logo">
				<IconsLogo />
			</nuxt-link>

			<div class="header__right">
				<nav class="header__nav" :class="{ 'header__nav--hidden': !showNav }">
					<ul class="header__nav-list">
						<li v-for="(link, index) in navLinks" :key="link.text + index">
							<UiNavLink :href="link.link">{{ link.text }}</UiNavLink>
						</li>
					</ul>
				</nav>

				<div
					class="header__burger"
					:class="[
						{ 'header__burger--visible': !showNav },
						burgerStage ? `header__burger--${burgerStage}` : '',
					]"
					@click="toggleMenu"
				></div>
			</div>
		</div>
	</header>
</template>

<style lang="scss">
.header {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	z-index: 1000;
	padding: 10px 0;

	&__container {
		height: 70px;
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	&__right {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: flex-end;
	}

	&__nav {
		transition: transform 0.3s ease, opacity 0.3s ease;
		transform: translateY(0);
		opacity: 1;
		pointer-events: auto;

		&--hidden {
			transform: translateY(-20px);
			opacity: 0;
			pointer-events: none;
		}

		&-list {
			display: flex;
			align-items: center;
			gap: 20px;
		}
	}

	&__burger {
		position: absolute;
		right: 0;
		top: 50%;
		transform: translateY(-50%) translateY(-20px);
		opacity: 0;
		pointer-events: none;
		width: 32px;
		height: 18px;
		cursor: pointer;
		transition: transform 0.3s ease, opacity 0.3s ease;

		&::before,
		&::after {
			content: "";
			position: absolute;
			right: 0;
			height: 2px;
			background-color: $white;
			transition: all 0.3s ease;
		}

		&::before {
			top: 0;
			width: 100%;
		}

		&::after {
			top: 9px;
			width: 70%;
		}

		&--visible {
			opacity: 1;
			transform: translateY(-50%) translateY(0);
			pointer-events: auto;
		}

		&--merge {
			&::before {
				top: 7px;
			}
			&::after {
				top: 7px;
				width: 100%;
			}
		}

		&--active {
			&::before {
				top: 7px;
				transform: rotate(45deg);
			}
			&::after {
				top: 7px;
				width: 100%;
				transform: rotate(-45deg);
			}
		}
	}
}
</style>
