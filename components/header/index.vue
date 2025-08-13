<script setup>
const navLinks = [
	{
		link: "#",
		text: "Кейсы",
	},
	{
		link: "#",
		text: "Услуги",
	},
	{
		link: "#",
		text: "Агенство",
	},
	{
		link: "#",
		text: "Блог",
	},
	{
		link: "#",
		text: "Вакансии",
	},
	{
		link: "#",
		text: "Контакты",
	},
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
	{
		icon: resolveComponent("IconsTg"),
		link: "#",
		text: "Написать в Telegram",
	},
	{
		icon: resolveComponent("IconsWhatsapp"),
		link: "#",
		text: "Написать в WhatsApp",
	},
];
</script>

<template>
	<!-- header -->
	<header class="header container">
		<nuxt-link to="/" class="header__logo">
			<IconsLogo />
		</nuxt-link>
		<nav class="header__nav">
			<ul class="header__nav-list">
				<li
					class="header__nav-item"
					v-for="(link, index) in navLinks"
					:key="link.text + index"
				>
					<UiNavLink :href="link.link">
						{{ link.text }}
					</UiNavLink>
				</li>
			</ul>
		</nav>
		<!-- <div class="header__burger">
      <span></span>
    </div> -->

		<!-- menu -->
		<!-- <div class="header__menu">
      <div class="header__menu-nav">
        <ul class="header__menu-list">
          <li
            class="header__menu-item"
            v-for="(link, index) in navLinks"
            :key="link.text + index"
          >
            <UiNavLink :href="link.link">
              {{ link.text }}
            </UiNavLink>
          </li>
        </ul>
      </div>
      <div class="header__menu-divider"></div>
      <div class="header__menu-contacts">
        <UiContactLink
          v-for="(item, index) in contactLinks"
          :key="index"
          :icon="item.icon"
          :link="item.link"
          :tabs="item.tabs || []"
					:light="item.light"
        >
          {{ item.text }}
        </UiContactLink>
      </div>
    </div> -->
	</header>
</template>

<style lang="scss">
.header
{
	margin: 0 auto;
	margin-top: 28px;
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: space-between;
	gap: 50px;

	.header__logo { z-index: 999; }

	.header__nav-list
	{
		display: flex;
		align-items: center;
		gap: 20px;
	}
	.header__burger { z-index: 999; }
	// .header__menu {
	// 	.header__menu-nav {
	// 	}
	// 	.header__menu-list {
	// 	}
	// 	.header__menu-item {
	// 	}
	// 	.header__menu-divider {
	// 	}
	// 	.header__menu-contacts {
	// 	}
	// }
}
</style>
