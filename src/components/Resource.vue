<template>
  <li>
    <BaseCard>
      <header>
        <h3>{{ resource.title }}</h3>
        <TheButton @click="handleDelete(resource.id)" title="Delete" />
      </header>
      <p>{{ resource.description }}</p>
      <nav><a :href="resource.link">View Resource</a></nav>
    </BaseCard>
  </li>
</template>

<script>
import BaseCard from './BaseCard.vue';
import TheButton from './TheButton.vue';
export default {
  name: 'Resource',
  data() {
    return {};
  },
  components: { BaseCard, TheButton },
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

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>