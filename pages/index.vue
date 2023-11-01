<script setup lang="ts">
import type { AllDocumentTypes, Content } from '~/prismicio-types'
import { components } from '~/slices'

const BLOG_PAGE: AllDocumentTypes['type'] = 'blogpage'
const { client } = usePrismic()

const { data: page } = await useAsyncData(`${BLOG_PAGE}`, () =>
  client.getSingle(BLOG_PAGE))

const DOCUMENT_TYPE: Content.BlogPageDocument['type'] = 'blogitems'

const { data: blogs } = await useAsyncData(DOCUMENT_TYPE, () =>
  client.getAllByType<Content.BlogPageDocument>(DOCUMENT_TYPE, {
    orderings: {
      field: 'document.first_publication_date',
      direction: 'desc',
    },
  }))
</script>

<template>
  <div class="bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl">
        <SliceZone v-if="page" :components="components" :slices="page.data.slices" />

        <div class="mt-10 border-t border-gray-200 pt-10 sm:mt-16 space-y-16 sm:pt-16">
          <ArticleListing :items="blogs" />
        </div>
      </div>
    </div>
  </div>
</template>
