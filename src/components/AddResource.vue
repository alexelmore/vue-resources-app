<template>
  <form ref="resourceForm" @submit.prevent="handleClick">
    <div>
      <label for="title">Resource Title:</label>
      <input required type="text" id="title" v-model="resource.title" />
    </div>

    <div>
      <label for="description">Resource Description:</label>
      <textarea
        name="description"
        id="description"
        required
        v-model="resource.description"
      ></textarea>
    </div>
    <div>
      <label for="link">Resource Link:</label>
      <input type="url" id="link" required v-model="resource.link" />
    </div>
    <div>
      <TheButton type="submit" title="Submit" />
    </div>
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

<style>
</style>