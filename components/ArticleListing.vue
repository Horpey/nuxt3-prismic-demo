<script lang="ts" setup>
import type { Content } from '@prismicio/client'

interface Props {
    items: Content.BlogitemsDocument<string>[] | null
}

defineProps<Props>()
</script>

<template>
    <section>
        <ArticleCard v-for="post in items" :key="post.id" :post="post" />
    </section>
</template>
