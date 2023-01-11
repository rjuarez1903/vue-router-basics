<template>
    <Title message="Blog Title"></Title>
    <ul>
        <li v-for="post in arrayBlog" :key="post.id">
            <router-link :to="`/blog/${post.id}`">
                {{ post.id }} - {{ post.title }}
            </router-link>
        </li>
    </ul>
</template>

<script>
    import Title from '@/components/Title.vue';

    export default {
        components: {
            Title
        },
        data() {
            return {
                arrayBlog: [],
            }
        },
        methods: {
            async consumeApi() {
                try {
                    const data = await fetch('https://jsonplaceholder.typicode.com/posts')
                    const array = await(data.json())
                    this.arrayBlog = array
                } catch (error) {
                    console.log(error)
                }
            }
        }, 
        created() {
            this.consumeApi()
        }
    }
</script>

<style scoped>
    ul {
        list-style: none;
        padding-left: 0;
    }
</style>