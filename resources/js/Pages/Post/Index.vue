<template>
    <div class="bg-gray-400 mx-auto w-2/3 p-8 m-8 rounded-full">
        <h2 class="text-lg text-center">Posts</h2>
        <div>
            <Link
                :href="route('post.create')"
                class="hover:bg-white hover:text-sky-500 block border border-sky-500 p-1 m-4 mx-auto w-32 bg-sky-400 rounded-full text-center text-gray-50">
                Add new post
            </Link>
        </div>
    </div>
    <div
        v-if="posts"
        class="w-1/3 mx-auto mb-8">
        <div
            v-for="post in posts"
            class="mt-6 pt-6 border-t border-gray-500">
            <div>id: {{ post.id }}</div>
            <div>title: {{ post.title }}</div>
            <div>content: {{ post.content }}</div>
            <div class="text-sm text-right">{{ post.date }}</div>
            <div class="text-sm text-right text-sky-500">
                <Link :href="route('post.show', post.id)">Show</Link>
            </div>
            <div class="text-sm text-right text-yellow-400">
                <Link :href="route('post.edit', post.id)">Edit</Link>
            </div>
            <div class="cursor-pointer text-sm text-right text-red-500">
                <p @click="del(post.id)">delete</p>
            </div>
        </div>
    </div>
</template>

<script>
import {Link} from "@inertiajs/inertia-vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

export default {
    name: "Index",
    layout: MainLayout,
    props: [
        'posts'
    ],
    components: {
        Link
    },
    methods: {
        del(id){
            this.$inertia.delete(`/posts/${id}`)
            alert('The post will be deleted!')
        }
    }
}
</script>

<style scoped>

</style>
