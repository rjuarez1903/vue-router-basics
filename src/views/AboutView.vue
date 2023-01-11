<template>
  <div class="about">
    <Title message="This is an about page"></Title>
  </div>
</template>

<script>
  import Title from '@/components/Title.vue';

  export default {
    name: 'AboutView',
    components: {
      Title
    }
  }
</script>