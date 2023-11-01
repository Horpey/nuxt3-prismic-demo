<script setup lang="ts">
import { defineProps } from 'vue'
import type { Content } from '@prismicio/client'
import { components } from '~/slices'

interface Props {
    post: Content.BlogitemsDocument
}

defineProps<Props>()

function formatDate(date: string) {
    const dateObj = new Date(date)
    return dateObj.toLocaleDateString('en', {
        month: 'long',
        day: 'numeric',
        year: 'numeric',
    })
}
</script>

<template>
    <article
        class="mb-12 max-w-xl flex flex-col items-start justify-between rounded-md p-3 transition-colors duration-200 ease-in-out hover:bg-[#F5E5FF]/50">
        <NuxtLink :to="`/posts/${post.uid}`">
            <div class="flex items-center gap-x-4 text-xs">
                <time :datetime="post.first_publication_date" class="text-gray-500">{{
                    formatDate(post.first_publication_date)
                }}</time>
            </div>

            <SliceZone v-if="post" :components="components" :slices="post.data.slices" />
        </NuxtLink>
    </article>
</template>
