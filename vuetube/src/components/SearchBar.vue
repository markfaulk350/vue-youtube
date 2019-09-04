<template>
  <div>
    <input @input="onInput" type="text" placeholder="Search..." />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput(event) { // Everytime this function is called, we are going to want to emit an event to parent component
      // console.log(event.target.value);
      this.$emit('termChange', event.target.value)
    }
  }
};
</script>

<style scoped>
</style>