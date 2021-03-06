<template>
  <base-card>
    <form v-on:submit.prevent="submitResource">
      <input v-model="resourceTitle" type="text" placeholder="title" />
      <input v-model="resourceDesc" type="text" placeholder="description" />
      <input v-model="resourceLink" type="text" placeholder="link" />
      <base-button>Add to resources</base-button>

      <error-alert v-if="inputIsValid">
        <h2>Input is invalid!</h2>
        <p>You have to add at least a title..</p>
        <button v-on:click="errorConfirmed">Gotcha!</button>
      </error-alert>
    </form>
  </base-card>
</template>

<script>
import ErrorAlert from '../ErrorAlert.vue';
import BaseCard from '../UI/BaseCard';
export default {
  components: { ErrorAlert, BaseCard },
  emits: ['submit-resource'],
  data: function() {
    return {
      resourceTitle: '',
      resourceDesc: '',
      resourceLink: '',
      inputIsValid: false
    };
  },
  methods: {
    submitResource() {
      if (this.resourceTitle === '') {
        this.inputIsValid = true;
      } else {
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
    },
    errorConfirmed() {
      this.inputIsValid = false;
    }
  }
};
</script>

<style></style>
