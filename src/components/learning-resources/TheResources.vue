<template>
  <base-card>
    <base-button v-on:click="setSelectedTab('stored-resources')">Stored Resources</base-button>
    <base-button v-on:click="setSelectedTab('add-resource')">Add Resources</base-button>
  </base-card>
</template>

<script>
export default {
  data: function() {
    return {
        selectedTab: 'stored-resources'
    };
  },
  methods: {
      setSelectedTab(tab) {
          this.selectedTab = tab;
      }
  }
};
</script>

<style></style>
BaseButton
