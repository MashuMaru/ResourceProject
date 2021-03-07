<template>
  <base-card>
    <base-button
      v-on:click="setSelectedTab('stored-resources')"
      v-bind:mode="storedResButtonMode">Stored Resources</base-button>
    <base-button
      v-on:click="setSelectedTab('add-resource')"
      v-bind:mode="addResButtonMode"
      >Add Resources</base-button>
  </base-card>
  <keep-alive>
    <component v-bind:is="selectedTab"></component>
  </keep-alive>
  <!-- <AddResource />
    <StoredResources /> -->
</template>

<script>
import StoredResources from './StoredResources';
import AddResource from './AddResource';
export default {
  components: { StoredResources, AddResource },
  data: function() {
    return {
      selectedTab: 'stored-resources',
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
  provide: function() {
    return {
      resources: this.storedResources,
      addResource: this.addResource
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url
      };
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    }
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resources' ? null : 'flat';
    }
  }
};
</script>

<style></style>
