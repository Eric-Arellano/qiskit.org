<template>
  <article class="feature-card">
    <h3 class="feature-card__title">
      {{ title }}
    </h3>
    <div class="feature-card__content">
      <div class="feature-card__image-container">
        <nuxt-img
          class="feature-card__image"
          format="webp"
          sizes="sm:300px md:600px lg:300px"
          alt=""
          :src="image"
        />
      </div>
      <!-- TODO: HTML content should not be in strings but in components
      but lacking of a better solution given time constraints. -->
      <!-- eslint-disable vue/no-v-html -->
      <div class="feature-card__description" v-html="description" />
      <!-- eslint-enable -->
    </div>
  </article>
</template>

<script setup lang="ts">
interface Props {
  image: string;
  title: string;
  description: string;
}

defineProps<Props>();
</script>

<style lang="scss" scoped>
@use "~/assets/scss/carbon.scss";

.feature-card {
  width: 100%;
  display: flex;

  @include carbon.breakpoint-down(lg) {
    flex-direction: column;
  }

  &__title {
    flex: 0 0 12rem;
    padding-right: carbon.$spacing-07;
    padding-bottom: carbon.$spacing-07;

    @include carbon.breakpoint-down(lg) {
      flex: 0 0 auto;
    }
  }

  &__content {
    min-height: 11rem;
    display: flex;

    @include carbon.breakpoint-down(md) {
      flex-direction: column;
    }
  }

  &__image {
    height: 100%;
    object-fit: contain;
    position: absolute;
    width: 100%;
  }

  &__image-container {
    flex: 0 0 14rem;
    overflow: hidden;
    position: relative;

    @include carbon.breakpoint-down(md) {
      height: 11rem;
    }
  }

  &__description {
    padding: carbon.$spacing-05 carbon.$spacing-05 carbon.$spacing-05
      carbon.$spacing-07;

    @include carbon.breakpoint-down(md) {
      padding: carbon.$spacing-06 0 0 0;
    }
  }
}
</style>
