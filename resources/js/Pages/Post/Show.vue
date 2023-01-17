<template>
 <div class="bg-gray-400 mx-auto w-2/3 p-8 m-8 rounded-full">
     <Link
         :href="route('post.index')"
         class="hover:bg-white hover:text-sky-500 block border border-sky-500 p-1 m-4 mx-auto w-32 bg-sky-400 rounded-full text-center text-gray-50">
         Back
     </Link>
     <h2 class="text-lg text-center">Post</h2>
     <div>


     </div>
 </div>
    <div
        v-if="post"
        class="w-1/3 mx-auto">
        <div class="mt-6 pt-6 border-t border-gray-500">
            <div>id:  {{post.id}}</div>
            <div>title:  {{post.title}}</div>
            <div>content:  {{post.content}}</div>
            <div class="text-sm text-right">{{post.date}}</div>
        </div>
    </div>
</template>

<script>
import {Link} from "@inertiajs/inertia-vue3";

export default {
    name: "Show",
    props: [
        'post'
    ],
    components: {
        Link
    }
}
</script>

<style scoped>

</style>
