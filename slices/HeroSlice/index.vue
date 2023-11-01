<script lang="ts" setup>
import type { HeroSliceSlice } from '~/prismicio-types'

interface Props {
  slice: HeroSliceSlice
}
defineProps<Props>()
</script>

<template>
  <section>
    <h2 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
      {{ slice.primary.heading }}
    </h2>
    <PrismicRichText :field="slice.primary.description" class="mt-2 text-xs leading-8 text-gray-600" />
  </section>
</template>
