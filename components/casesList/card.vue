<template>
  <nuxt-link class="case-card" to="#" :style="{ backgroundImage: `url(${card.img})` }">
    <div class="case-card__categories">
      <div class="categories-slider">
        <span v-for="category in card.categories" :key="category">{{ category }}</span>
      </div>
    </div>

    <div class="case-card__title">{{ card.title }}</div>

    <div class="case-card__icon" v-if="card.foreign">
      <IconsForeign />
    </div>
  </nuxt-link>
</template>

<script setup>
const props = defineProps({
  card: {
    type: Object,
    required: true,
    default: () => ({})
  },
});
</script>

<style lang="scss" scoped>
.case-card {
  position: relative;
  padding: 24px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 100%;
  aspect-ratio: 3/4;
  background-size: cover;
  background-position: center;
  border-radius: 20px;
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.5s ease;

  // фон зумится на hover
  &:hover {
    background-size: 110%;
  }

  &__categories {
    width: 100%;
    overflow: hidden;
    max-height: 0;
    opacity: 0;
    transition: all 0.7s ease;
    margin-bottom: 10px;

    .categories-slider {
      display: flex;
      gap: 20px;
      white-space: nowrap;
      animation: slide 6s linear infinite alternate;

      span {
        display: inline-block;
        padding: 4px 12px;
        background: rgba(0, 0, 0, 0.55);
        border-radius: 10px;
        color: white;
        font-size: 14px;
        font-weight: 500;
      }
    }
  }

  &__title {
    font-size: 18px;
    font-weight: 500;
    line-height: 130%;
    color: #fff;
    z-index: 2;
    transition: transform 0.7s ease;
  }

  &__icon {
    position: absolute;
    bottom: 40px;
    left: 30px;
    z-index: 2;
  }

  // hover эффекты
  &:hover {
    .case-card__title {
      transform: translateY(20px);
    }

    .case-card__categories {
      max-height: 40px;
      opacity: 1;
    }
  }
}

// анимация категорий туда-сюда
@keyframes slide {
  0% {
    transform: translateX(0%);
  }
  50% {
    transform: translateX(-20%);
  }
  100% {
    transform: translateX(0%);
  }
}
</style>
