<template>
  <button>
    <slot> </slot>
  </button>
</template>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: rgb(249, 142, 2);
  border: 1px solid rgb(249, 142, 2);
  border-radius: 1000px;
  color: white;
  font-size: 3rem;
  cursor: pointer;
  padding: 0 1rem;
}

button:hover,
button:active {
  background-color: rgb(164, 20, 247);
  background-color: rgb(164, 20, 247);
}
</style>
