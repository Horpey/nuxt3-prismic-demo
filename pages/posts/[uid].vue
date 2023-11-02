<script lang="ts" setup>
import { useRoute } from 'vue-router'
import { usePrismic } from '@prismicio/vue'
import type { Content } from '@prismicio/client'
import { computed, ref } from 'vue'
import { components } from '~/slices'

const { client } = usePrismic()
const route = useRoute()

const UID = route.params.uid as string
const DOCUMENT_TYPE: Content.BlogitemsDocument['type'] = 'blogitems'

const { data: page } = await useAsyncData(`${DOCUMENT_TYPE}_${UID}`, () =>
    client.getByUID(DOCUMENT_TYPE, UID))

if (!page.value) {
    throw createError({
        fatal: true,
        statusCode: 404,
        statusMessage: 'Not Found',
        message: 'The requested document was not found.',
    })
}

const pageData = computed(() => page.value?.data?.slices[0]?.primary)
</script>

<template>
    <div class="bg-white py-24 sm:py-32">
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <div v-if="page" class="mx-auto max-w-2xl">
                <div class="mb-6">
                    <NuxtLink to="/">
                        ← View all posts
                    </NuxtLink>
                </div>

                <h2 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
                    {{ pageData?.title }}
                </h2>
                <PrismicRichText :field="pageData?.excerpt" class="mt-2 text-sm text-gray-600" />

                <div class="relative mt-8 flex items-center gap-x-4">
                    <span class="inline-block h-6 w-6 overflow-hidden rounded-full bg-gray-100">
                        <svg class="h-full w-full text-gray-300" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z" />
                        </svg>
                    </span>

                    <div v-if="pageData?.author" class="text-sm leading-6">
                        <p class="font-semibold text-gray-900">
                            <span class="absolute inset-0" />
                            {{ pageData?.author }}
                        </p>
                        <p class="text-gray-600">
                            Author
                        </p>
                    </div>
                </div>

                <div class="mt-10">
                    <PrismicImage v-if="pageData?.banner" :field="pageData?.banner"
                        class="h-auto w-full rounded-md bg-gray-50" />

                    <PrismicRichText :field="pageData?.description" class="mt-10 text-lg leading-9" />
                </div>

                <pre>
                    {{ pageData }}
                </pre>
            </div>
        </div>
    </div>
</template>
