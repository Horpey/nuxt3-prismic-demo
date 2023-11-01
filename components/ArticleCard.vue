<script setup lang="ts">
import { defineProps } from 'vue'

interface Props {
    post: {
        id: number
        title: string
        slug: string
        description: string
        date: string
        datetime: string
        category: {
            title: string
        }
        author: {
            name: string
            role: string
            imageUrl: string
        }
    }
}

defineProps<Props>()
</script>

<template>
    <article class="max-w-xl flex flex-col items-start justify-between">
        <div class="flex items-center gap-x-4 text-xs">
            <time :datetime="post.datetime" class="text-gray-500">{{ post.date }}</time>
            <NuxtLink :to="`/posts/${post.slug}`"
                class="relative z-10 rounded-full bg-gray-50 px-3 py-1.5 font-medium text-gray-600 hover:bg-gray-100">
                {{
                    post.category.title }}
            </NuxtLink>
        </div>
        <div class="group relative">
            <h3 class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600">
                <NuxtLink :to="`/posts/${post.slug}`">
                    <span class="absolute inset-0" />
                    {{ post.title }}
                </NuxtLink>
            </h3>
            <p class="line-clamp-3 mt-5 text-sm leading-6 text-gray-600">
                {{ post.description }}
            </p>
        </div>
        <div class="relative mt-8 flex items-center gap-x-4">
            <img :src="post.author.imageUrl" alt="" class="h-10 w-10 rounded-full bg-gray-50">
            <div class="text-sm leading-6">
                <p class="font-semibold text-gray-900">
                    <span class="absolute inset-0" />
                    {{ post.author.name }}
                </p>
                <p class="text-gray-600">
                    {{ post.author.role }}
                </p>
            </div>
        </div>
    </article>
</template>
