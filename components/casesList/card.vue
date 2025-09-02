<script setup>
const props = defineProps({
  card: {
    type: Object,
    required: true,
    default: () => ({})
  },
	blackText: {
		type: Boolean,
		default: false
	}
});
</script>

<template>
  <nuxt-link class="case-card" to="#">
    <div class="case-card__bg" :style="{ backgroundImage: `url(${card.img})` }"></div>
    <div class="case-card__categories">
      <div class="case-card__categories-slider" :class="{'case-card__categories-slider--black': blackText}">
        <span v-for="category in card.categories" :key="category">{{ category }}</span>
      </div>
    </div>
    <div class="case-card__title" :class="{'case-card__title--black': blackText}">{{ card.title }}</div>
    <div class="case-card__icon" v-if="card.foreign">
      <IconsForeign />
    </div>
  </nuxt-link>
</template>

<style lang="scss" scoped>
.case-card
{
  position: relative;
  padding: 24px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 100%;
  aspect-ratio: 3/4;
  border-radius: 30px;
  overflow: hidden;
  cursor: pointer;

  .case-card__bg
	{
    position: absolute;
    inset: 0;
    background-size: cover;
    background-position: center;
    transition: transform 0.7s ease;
    z-index: 0;
  }

  &:hover .case-card__bg { transform: scale(1.1); }

  &__categories
	{
    width: 100%;
    max-height: 0;
    opacity: 0;
    transition: all 1s ease;
    margin-bottom: 10px;

    .case-card__categories-slider
		{
      display: flex;
      gap: 20px;
      white-space: nowrap;
      animation: slide 6s linear infinite alternate;

      span
			{
        display: inline-block;
        color: $white;
        font-size: 14px;
        font-weight: 300;
				line-height: 140%;
      }

			&--black span { color: $black; }
    }
  }

  &__title
	{
    font-size: 20px;
    font-weight: 500;
    line-height: 150%;
    color: #fff;
    z-index: 2;
    transition: transform 0.7s ease;

		&--black { color: $black; }
  }

  &__icon
	{
    position: absolute;
    bottom: 40px;
    left: 30px;
    z-index: 2;
  }

  &:hover
	{
    .case-card__title { transform: translateY(20px); }

    .case-card__categories
		{
      max-height: 40px;
      opacity: 1;
    }
  }
}

@keyframes slide
{
  0% { transform: translateX(0%); }

  50% { transform: translateX(-20%); }

  100% { transform: translateX(0%); }
}
</style>
