<template>
  <BaseCard>
    <TheButton type="button" @click="toggleResource(false)">
      Store Resources</TheButton
    >

    <TheButton type="button" @click="toggleResource(true)">
      Add Resource</TheButton
    >
  </BaseCard>
</template>

<script>
import BaseCard from './BaseCard.vue';
import TheButton from './TheButton.vue';
export default {
  name: 'ResourcesTab',
  components: {
    BaseCard,
    TheButton,
  },
  data() {
    return {
      showResources: false,
    };
  },
  methods: {
    toggleResource(status) {
      this.$emit('show-resource', status);
    },
  },
  emits: {
    'show-resource': String,
  },
};
</script>

<style>
</style>