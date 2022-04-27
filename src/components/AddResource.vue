<template>
  <form ref="resourceForm" @submit.prevent="handleClick">
    <label for="title">Resource Title:</label>
    <input required type="text" id="title" v-model="resource.title" />

    <label for="description">Resource Description:</label>
    <textarea
      name="description"
      id="description"
      required
      v-model="resource.description"
    ></textarea>

    <label for="link">Resource Link:</label>
    <input type="url" id="link" required v-model="resource.link" />

    <TheButton type="submit"> Submit</TheButton>
  </form>
</template>

<script>
import TheButton from '../components/TheButton.vue';

export default {
  name: 'AddResource',
  components: { TheButton },
  data() {
    return {
      resource: {
        title: '',
        description: '',
        link: '',
        id: '',
      },
    };
  },
  methods: {
    handleClick() {
      this.resource.id = this.constructId;
      let newResource = this.resource;
      this.$emit('new-resource', newResource);
      this.$refs.resourceForm.reset();
    },
  },
  emits: {
    'new-resource': String,
  },
  computed: {
    constructId() {
      let id = Math.floor(Math.random() * 1000);
      return `${this.resource.title.toLowerCase()}-${id}`;
    },
  },
};
</script>

<style scoped>
form {
  width: fit-content;
  margin: auto;
  min-width: 25rem;
}
button {
  width: fit-content;
  margin: 0 auto;
  display: block;
}
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}
input {
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