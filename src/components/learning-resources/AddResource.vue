<template>
  <base-dialog v-if="inputIsInvalid" title="Invalid Input" v-on:close="confirmError">
    <template v-slot:default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>
        Please check all inputs and make sure you enter at least a few
        characters into each input field.
      </p>
    </template>
    <template v-slot:actions>
      <base-button v-on:click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form v-on:submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>

      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div>
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div>
        <base-button type="submit">Add Resources</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
// import BaseCard from '../UI/BaseCard';
export default {
  // components: { BaseCard },
  inject: ['addResource'],
  data: function() {
    return {
      inputIsInvalid: false
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descInput.value;
      const enteredURL = this.$refs.linkInput.value;
      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredURL === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }
      this.addResource(enteredTitle, enteredDescription, enteredURL);
    },
    confirmError() {
      this.inputIsInvalid = false;
    }
  }
};
</script>

<style>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
