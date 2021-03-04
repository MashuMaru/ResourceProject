<template>
  <ul>
    <LearningResource
      v-for="res in storedResources"
      v-bind:key="res.id"
      v-bind:title="res.title"
      v-bind:description="res.description"
      v-bind:link="res.link"
    />
  </ul>
</template>

<script>
import LearningResource from './components/learning-resources/LearningResource.vue';

export default {
  components: { LearningResource },

  data: function() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn how to search with Google...',
          link: 'https://google.com'
        }
      ]
    };
  }
};
</script>

<style></style>
