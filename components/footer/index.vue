<script setup>
import IconsFb from "@/components/icons/fb.vue";
import IconsVk from "@/components/icons/vk.vue";
import IconsInsta from "@/components/icons/insta.vue";
import IconsTg from "@/components/icons/tg.vue";

const socialsLinks = [IconsFb, IconsVk, IconsInsta, IconsTg];

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

const feedbackLinks = [
	{ text: "Telegram", link: "#" },
	{ text: "WhatsApp", link: "#" },
];
</script>

<template>
  <div class="footer container">
    <div class="footer__contacts">
      <ul class="footer__contacts-list">
        <UiContactLink
          v-for="(link, index) in contactLinks"
          :key="index"
          :link="link.link"
          :tabs="link.tabs"
          inline
          class="footer__contacts-item"
        >
          {{ link.text }}
        </UiContactLink>
      </ul>

      <div class="footer__contacts-feedback">
        <span class="footer__contacts-feedback-text">Связаться</span>
        <div class="footer__contacts-feedback-links">
          <nuxt-link
            v-for="link in feedbackLinks"
            :key="link.text"
            :to="link.link"
            class="footer__contacts-feedback-link"
          >
            {{ link.text }}
          </nuxt-link>
        </div>
      </div>
    </div>

    <div class="footer__socials">
			<span>Связаться с нами:</span>
      <div class="footer__socials-list">
				<nuxt-link
					v-for="(social, index) in socialsLinks"
					:key="index"
					to="/"
					class="footer__socials-link"
				>
					<component :is="social" />
				</nuxt-link>
			</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.footer
{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 60px;

  .footer__contacts
	{
    display: flex;
    align-items: center;
    gap: 50px;

		@media(max-width: 1024px) { display: none; }
  }

  .footer__contacts-feedback
	{
    position: relative;
    display: flex;
    align-items: center;
    gap: 20px;
    font-size: 16px;
    font-weight: 300;
    line-height: 140%;
    color: $link;
    cursor: pointer;

		@media(max-width: 1024px) { display: none; }

    .footer__contacts-feedback-text,
    .footer__contacts-feedback-links
		{
			text-decoration: underline;
      display: inline-block;
      transition: opacity 0.3s ease, transform 0.3s ease;
    }

    .footer__contacts-feedback-links
		{
      opacity: 0;
      position: absolute;
      top: 0;
      left: 0;
      display: flex;
      gap: 10px;
      transform: translateY(10px);
      pointer-events: none;
    }

    &:hover .footer__contacts-feedback-text
		{
      opacity: 0;
      transform: translateY(-10px);
    }

    &:hover .footer__contacts-feedback-links
		{
      opacity: 1;
      transform: translateY(0);
      pointer-events: auto;
    }

    .footer__contacts-feedback-link
		{
      text-decoration: underline;
      color: $link;
    }
  }

  .footer__socials
	{
    display: flex;
    align-items: start;
    gap: 30px;

		@include tablet
		{
			flex-direction: column;
			gap: 20px;
		}

		span
		{
			display: none;
			font-size: 16px;
			font-weight: 300;
			line-height: 140%;
			color: $disabled;

			@include tablet { display: block; }
		}
  }

	.footer__socials-list
	{
		display: flex;
    align-items: center;
    gap: 30px;
	}

	.footer__socials-link
	{
		opacity: .5;
		transition: opacity .3s ease;

		&:hover { opacity: 1; }
	}
}
</style>
