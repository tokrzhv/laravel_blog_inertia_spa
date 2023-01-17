<template>
    <div class="bg-gray-400 mx-auto w-2/3  p-8 m-8 rounded-full">
        <Link
            :href="route('post.index')"
            class="hover:bg-white hover:text-sky-500 block border border-sky-500 p-1 m-4 mx-auto w-32 bg-sky-400 rounded-full text-center text-gray-50">
            Back
        </Link>
        <h2 class="text-lg text-center">Edit</h2>
        <form @click.prevent="update" class="mt-3 mx-auto w-2/3">
            <div class="mb-2">
                <input v-model="title" class="rounded-full  mx-auto w-full" type="text" placeholder="title">
                <div v-if="errors.title" class="text-red-600 text-sm">{{errors.title}}</div>
            </div>
            <div class="mb-2">
                <textarea v-model="content" class="mx-auto w-full rounded-full" placeholder="content"></textarea>
                <div v-if="errors.content" class="text-red-600 text-sm">{{errors.content}}</div>
            </div>
            <div class="mb-2 flex">
                <button
                    class="hover:bg-white hover:text-green-500 block border border-green-500 p-1 m-4 ml-auto w-32 bg-green-400 rounded-full text-center text-white"
                    type="submit">Update
                </button>
            </div>

        </form>
    </div>
</template>

<script>
import {Link} from "@inertiajs/inertia-vue3";

export default {
    name: "Create",
    data(){
        return{
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,
        }
    },
    props: [
        'post',
        'errors',
    ],
    components: {
        Link
    },
    methods: {
        update(){
            this.$inertia.patch(`/posts/${this.id}`, {title:this.title, content: this.content})
        }
    }
}
</script>

<style scoped>
body {
    background-color: #6b7280;
}
</style>
