<script setup>
import IconsFb from "@/components/icons/fb.vue";
import IconsVk from "@/components/icons/vk.vue";
import IconsInsta from "@/components/icons/insta.vue";
import IconsTg from "@/components/icons/tg.vue";

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
		link: "#",
		tabs: [
			{ label: "Москва", value: "Позвонить +7-(999)-999-99-99" },
			{ label: "Санкт-Петербург", value: "Позвонить +7-(888)-888-88-88" },
		],
		light: true,
	},
];
const modalButtons = [{ text: "Отправить заявку" }, { text: "Написать в чат" }];
const socialsLinks = [IconsFb, IconsVk, IconsInsta, IconsTg];

const showNav = ref(true);
const burgerStage = ref("");
const isModalOpen = ref(false);

const handleScroll = () => {
	showNav.value = window.scrollY === 0;
};

const toggleMenu = () => {
	if (burgerStage.value === "") {
		burgerStage.value = "merge";
		isModalOpen.value = true;
		setTimeout(() => {
			burgerStage.value = "active";
		}, 150);
	} else {
		burgerStage.value = "merge";
		isModalOpen.value = false;
		setTimeout(() => {
			burgerStage.value = "";
		}, 150);
	}
};

watch(isModalOpen, (newValue) => {
	if (newValue) {
		document.body.classList.add("no-scroll");
	} else {
		document.body.classList.remove("no-scroll");
	}
});

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
		<div class="header__modal" v-if="isModalOpen" @click="toggleMenu">
			<div class="header__modal-wrapper" @click="toggleMenu">
				<nav class="header__modal-nav" @click.stop>
					<ul class="header__modal-nav-list">
						<li
							v-for="(link, index) in navLinks"
							:key="link.text + index + ' modal'"
							class="header__modal-nav-item"
						>
							<UiNavLink :href="link.link" :is-large="true">
								{{ link.text }}
							</UiNavLink>
						</li>
					</ul>
				</nav>
				<div class="header__modal-buttons" @click.stop>
					<UiButton
						v-for="(button, index) in modalButtons"
						:key="button.text + index"
					>
						{{ button.text }}
					</UiButton>
				</div>
				<div class="header__modal-footer" @click.stop>
					<div class="header__modal-footer-contacts">
						<UiContactLink
							v-for="(link, index) in contactLinks"
							:key="index"
							:link="link.link"
							:tabs="link.tabs"
							>{{ link.text }}
						</UiContactLink>
					</div>
					<div class="header__modal-footer-social">
						<nuxt-link
							v-for="(social, index) in socialsLinks"
							:key="index"
							to="/"
							class="header__modal-footer-social-link"
						>
							<component :is="social" />
						</nuxt-link>
					</div>
				</div>
			</div>
		</div>
	</header>
</template>

<style lang="scss">
.header
{
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	z-index: 1000;
	padding: 10px 0;

	&__container
	{
		height: 70px;
		max-width: 1573px;
		margin: 0 auto;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0;

		@media(max-width: 1600px) {
			max-width: 1233px;
		}

		@media(max-width: 1366px) {
			max-width: 1214px;
			padding: 0 30px;
		}
	}

	&__right
	{
		max-width: max-content;
		position: relative;
		display: flex;
		align-items: center;
		justify-content: flex-end;
	}

	&__logo { z-index: 1000; }

	&__nav
	{
		transition: transform 0.3s ease, opacity 0.3s ease;
		transform: translateY(0);
		opacity: 1;
		pointer-events: auto;

		&--hidden
		{
			transform: translateY(-20px);
			opacity: 0;
			pointer-events: none;

			@media(max-width: 820px) { display: none; }
		}

		&-list
		{
			display: flex;
			align-items: center;
			gap: 20px;

			@media(max-width: 900px) { display: none; }
		}
	}

	&__burger
	{
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
		z-index: 1000;

		@media(max-width: 900px)
		{
			opacity: 1;
			transform: translateY(-50%) translateY(0);
			pointer-events: auto;
		}

		&::before,
		&::after
		{
			content: "";
			position: absolute;
			right: 0;
			height: 2px;
			background-color: $white;
			transition: all 0.3s ease;
		}

		&::before
		{
			top: 0;
			width: 100%;
		}

		&::after
		{
			top: 9px;
			width: 70%;
		}

		&--visible
		{
			opacity: 1;
			transform: translateY(-50%) translateY(0);
			pointer-events: auto;
		}

		&--merge
		{
			&::before { top: 7px; }

			&::after
			{
				top: 7px;
				width: 100%;
			}
		}

		&--active
		{
			&::before
			{
				top: 7px;
				transform: rotate(45deg);
			}

			&::after
			{
				top: 7px;
				width: 100%;
				transform: rotate(-45deg);
			}
		}
	}

	.header__modal
	{
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		z-index: 100;
		display: flex;
		align-items: center;
		justify-content: center;

		&::before
		{
			content: "";
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background-color: rgba($color: $dark, $alpha: 0.7);
			backdrop-filter: blur(20px);
			z-index: -1;
		}

		.header__modal-wrapper
		{
			display: flex;
			padding: 310px 75px 30px;
			flex-direction: column;
			gap: 90px;
			z-index: 11;
			width: 100%;
			height: 100%;

			@media (max-width: 1024px) { padding: 172px 75px 30px; }

			@media (max-width: 768px)
			{
				padding: 150px 30px 85px;
				align-items: flex-start;
				gap: 50px;
			}

			@media (max-width: 450px)
			{
				padding: 150px 10px 85px;
				gap: 40px;
			}
		}

		.header__modal-nav-list
		{
			display: flex;
			align-items: center;
			justify-content: center;
			gap: 10px;

			@media (max-width: 1024px)
			{
				flex-direction: column;
				gap: 25px;
			}

			@media (max-width: 768px) { align-items: flex-start; }
		}

		.header__modal-buttons
		{
			display: flex;
			align-items: center;
			justify-content: center;
			gap: 20px;

			@media (max-width: 768px) { margin-left: 30px; }

			@media (max-width: 450px)
			{
				flex-direction: column;
				align-items: flex-start;
			}
		}

		.header__modal-footer
		{
			width: 100%;
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin-top: auto;

			@media (max-width: 768px)
			{
				margin: 0;
				margin-left: 30px;
				flex-direction: column;
				align-items: flex-start;
				gap: 20px;
			}
		}

		.header__modal-footer-contacts
		{
			display: flex;
			align-items: center;
		}

		.header__modal-footer-social
		{
			display: flex;
			align-items: center;
			gap: 30px;

			a
			{
				opacity: 0.5;
				transition: all 0.2s ease;

				&:hover { opacity: 1; }
			}
		}
	}
}
</style>
