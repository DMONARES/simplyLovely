<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
    default: () => ({})
  },
  layout: {
    type: String,
    default: 'grid',
  },
  headerVariant: {
    type: String,
    default: 'column'
  }
});
</script>

<template>
  <section class="cases-block container section">
    <CasePartsHeader
      :data="data.header"
      :variant="headerVariant"
    />

    <CaseLayoutsGrid
      v-if="layout === 'grid'"
      :cases="data.cases"
      :last-card-text="data.lastCardText"
    />

    <CaseLayoutsSlider
      v-else-if="layout === 'slider'"
      :cases="data.cases"
			:last-card-text="data.lastCardText"
      :square="data.squareCards"
    />
  </section>
</template>

<style lang="scss" scoped>
.cases-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 95px;

  @include tablet { gap: 80px; }
  @include mobile { gap: 40px; }
}
</style>