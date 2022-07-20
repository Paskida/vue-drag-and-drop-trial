<template>
  <section>
    <the-header title="Teams"></the-header>
    <div>
      <team-column></team-column>
    </div>
  </section>
</template>

<script>
import TheHeader from "./components/Layout/TheHeader.vue";
import TeamColumn from "./components/TeamColumn.vue";
export default {
  components: { TheHeader, TeamColumn },
  data() {
    return {};
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 2rem 2rem;
}

h1 {
  font-size: 3rem;
}
</style>
