<template>
  <div>
    <button @click="toggleResource = false">Store Resources</button>
    <button @click="toggleResource = true">Add Resource</button>
  </div>
  <div v-if="toggleResource"><AddResource @newResource="addResource" /></div>
  <div v-else>
    <ul v-for="resource in resources" :key="resource">
      <Resource :resource="resource" @removeResource="deleteResource" />
    </ul>
  </div>
</template>

<script>
import AddResource from './components/AddResource.vue';
import Resource from './components/Resource.vue';
export default {
  name: 'App',
  data() {
    return {
      resources: [
        {
          title: 'Google',
          description: 'Learning with Google',
          link: 'https://www.google.com/',
          id: 'google-12345',
        },
        {
          title: 'Udemy',
          description: 'Learning with Udemy',
          link: 'https://www.udemy.com/',
          id: 'udemy-12345',
        },
      ],
      toggleResource: false,
    };
  },
  components: {
    AddResource,
    Resource,
  },
  methods: {
    addResource(val) {
      let isPresent = this.resources.find((res) => {
        return res.id === val.id;
      });
      if (isPresent === undefined) {
        this.resources.push(val);
      } else {
        alert(`You already a resource with this id: ${val.id}`);
      }
    },
    deleteResource(val) {
      this.resources = this.resources.filter((r) => r.id !== val);
    },
  },
};
</script>

<style>
</style>