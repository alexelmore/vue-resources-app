<template>
  <li>
    <h2>{{ resource.title }}</h2>
    <p>{{ resource.description }}</p>
    <a :href="resource.link">View Resource</a>
  </li>
  <button @click="handleDelete(resource.id)">Delete</button>
</template>

<script>
export default {
  name: 'Resource',
  data() {
    return {};
  },
  props: {
    resource: Object,
  },
  emits: {
    'remove-resource': String,
  },
  methods: {
    handleDelete(id) {
      this.$emit('remove-resource', id);
    },
  },
};
</script>

<style>
</style>