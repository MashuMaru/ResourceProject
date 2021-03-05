<template>
  <TheHeader title="Resource Links"/>
  <AddResource v-on:submit-resource="submitResource" />
  <StoredResources v-bind:resources="storedResources" />
</template>

<script>
import StoredResources from './components/learning-resources/StoredResources.vue';
import AddResource from './components/learning-resources/AddResource.vue';
import TheHeader from './components/Layouts/TheHeader';

export default {
  components: { StoredResources, AddResource, TheHeader },

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
  },
  methods: {
    submitResource(title, desc, link) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: desc,
        link: link
      };
      this.storedResources.push(newResource);
    }
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
