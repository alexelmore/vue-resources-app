<template>
  <TheHeader title="Vue Resources" />
  <div>
    <button @click="toggleResource = false">Store Resources</button>
    <button @click="toggleResource = true">Add Resource</button>
  </div>
  <div v-if="toggleResource"><AddResource @newResource="addResource" /></div>
  <div v-else>
    <ul v-for="resource in resources" :key="resource.id">
      <Resource :resource="resource" @removeResource="deleteResource" />
    </ul>
  </div>
</template>

<script>
import AddResource from './components/AddResource.vue';
import Resource from './components/Resource.vue';
import TheHeader from './components/TheHeader.vue';

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
    TheHeader,
  },
  methods: {
    addResource(val) {
      let isPresent = this.resources.find((res) => {
        return res.id === val.id;
      });
      if (isPresent === undefined) {
        this.resources.push(val);
      } else {
        alert(`You already have a resource with this id: ${val.id}`);
      }
    },
    deleteResource(val) {
      this.resources = this.resources.filter((r) => r.id !== val);
    },
  },
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
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>