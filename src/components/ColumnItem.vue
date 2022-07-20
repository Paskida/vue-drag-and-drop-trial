<template>
  <li>{{ name }}</li>
</template>

<script>
export default {
  props: ["name"],
};
</script>

<style scoped>
li {
  list-style-type: none;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  padding-bottom: 2rem;
  margin: 2rem auto;
  background-color: rgb(249, 250, 250);
}
</style>
