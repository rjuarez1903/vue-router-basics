<template>
    <Title message="Article"></Title>
    <h2>Parameter: {{ $route.params.id }}</h2>
    <h2>{{ article.title }}</h2>
    <p>{{ article.body }}</p>

</template>

<script>
    import Title from '@/components/Title.vue';

    export default {
        components: {
            Title
        },
        data() {
            return {
                article: {}
            }
        },
        methods: {
            async consumeArticle() {
                try {
                    const data   = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                    const object = await data.json()
                    this.article  = object
                } catch (error) {
                    console.log(error)
                }
            }
        }, 
        created() {
            this.consumeArticle()
        }
    }
</script>

<style scoped>

</style>