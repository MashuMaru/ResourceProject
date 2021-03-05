<template>
  <div>
    <form v-on:submit.prevent="submitResource">
      <input v-model="resourceTitle" type="text" placeholder="title" />
      <input v-model="resourceDesc" type="text" placeholder="description" />
      <input v-model="resourceLink" type="text" placeholder="link" />
      <base-button>Add to resources</base-button>
    </form>
  </div>
</template>

<script>
export default {
  emits: ['submit-resource'],
  data: function() {
    return {
      resourceTitle: '',
      resourceDesc: '',
      resourceLink: ''
    };
  },
  methods: {
    submitResource() {
      this.$emit(
        'submit-resource',
        this.resourceTitle,
        this.resourceDesc,
        this.resourceLink
      );
      (this.resourceTitle = ''),
        (this.resourceDesc = ''),
        (this.resourceLink = '');
    }
  }
};
</script>

<style></style>
