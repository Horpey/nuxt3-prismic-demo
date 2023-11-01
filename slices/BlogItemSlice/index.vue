<script lang="ts" setup>
import type { BlogItemSlice } from '~/prismicio-types'

interface Props {
  slice: BlogItemSlice
}
defineProps<Props>()
</script>

<template>
  <div>
    <div class="group relative">
      <h3 class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600">
        {{ slice.primary.title }}
      </h3>
      <div>
        <span class="text-xs uppercase">
          {{
            slice.primary.category
          }}
        </span>
      </div>

      <PrismicRichText :field="slice.primary.excerpt" class="line-clamp-3 mt-5 text-sm leading-6 text-gray-600" />
    </div>
    <div class="relative mt-2 flex items-center gap-x-4">
      <span class="inline-block h-6 w-6 overflow-hidden rounded-full bg-gray-100">
        <svg class="h-full w-full text-gray-300" fill="currentColor" viewBox="0 0 24 24">
          <path
            d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z" />
        </svg>
      </span>

      <div class="text-sm leading-6">
        <p class="font-semibold text-gray-900">
          <span class="absolute inset-0" />
          {{ slice.primary.author }}
        </p>
        <p class="text-gray-600">
          Author
        </p>
      </div>
    </div>
  </div>
</template>
