<script setup lang="ts">
import { ref } from 'vue'

const post = ref({
    id: 1,
    title: 'Boost your conversion rate',
    slug: 'boost-your-conversion-rate',
    description:
        'Illo sint voluptas. Error voluptates culpa eligendi. Hic vel totam vitae illo. Non aliquid explicabo necessitatibus unde. Sed exercitationem placeat consectetur nulla deserunt vel iusto corrupti dicta laboris incididunt.',
    date: 'Mar 16, 2020',
    datetime: '2020-03-16',
    category: { title: 'Marketing', href: '#' },
    author: {
        name: 'Michael Foster',
        role: 'Co-Founder / CTO',
        imageUrl:
            'https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80',
    },
    banner: 'https://images.pexels.com/photos/12916314/pexels-photo-12916314.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
})
</script>

<template>
    <div class="bg-white py-24 sm:py-32">
        <div class="mx-auto max-w-7xl px-6 lg:px-8">
            <div class="mx-auto max-w-2xl">
                <div class="mb-6">
                    <NuxtLink to="/">
                        ← View all posts
                    </NuxtLink>
                </div>

                <h2 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
                    Boost your conversion rate
                </h2>
                <p class="mt-2 text-sm text-gray-600">
                    Illo sint voluptas. Error voluptates culpa eligendi. Hic vel totam vitae illo. Non aliquid explicabo
                    necessitatibus unde. Sed exercitationem placeat consectetur nulla deserunt vel iusto corrupti dicta
                    laboris incididunt.
                </p>

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

                <div class="mt-10">
                    <img :src="post.banner" alt="" class="h-auto w-full rounded-md bg-gray-50">

                    <div class="mt-10 text-lg leading-9">
                        I’m currently writing a talk about story in New Yorker cartoons, which I will deliver next week at
                        Dreamworks. It’s an honor to speak to their creative community — I just hope I can impart something
                        new! Here are parts of what I will say.

                        Story is everywhere. In single panel cartoons, they have to be kept in one image. It’s tricky and
                        challenging and I love it. I like to say that a single panel cartoon is like a mini stage. The
                        artist is a set designer, choreographer, script writer, costume designer, casting director. Each
                        element in the drawing needs to be necessary for the idea, no more, no less; there are exceptions of
                        course. Some creators are known for a style that is overly detailed and complicated, and that is
                        part of the voice of the artist and contributes to the story. The image is one moment in time, and
                        you have to feel that there is time before the moment you see, and a continuation after that moment.
                        And the characters are well “described” in the execution.

                        There are so many elements at work in a good single panel cartoon. I don’t always follow what I am
                        telling you, but I try. Here are a few other thoughts I will be speaking about, using my work in The
                        New Yorker as example.
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
