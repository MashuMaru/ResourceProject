<template>
  <li>
    <div>
      <header>
        <h3>{{ title }}</h3>
        <button>Delete</button>
      </header>
    </div>
    <p>{{ description }}</p>
    <nav>
      <a v-bind:href="link" target="_blank">Link resource.</a>
    </nav>
  </li>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    description: {
      type: String
    },
    link: {
      type: String
    }
  }
};
</script>

<style></style>
