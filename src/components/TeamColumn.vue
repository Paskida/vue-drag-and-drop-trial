<template>
  <div class="card">
    <div class="column">
      <!--1 column-->
      <h3>Product Management</h3>
      <draggable
        id="first"
        data-source="juju"
        :list="list"
        group="a"
        item-key="name"
        @dragover.prevent
        @dragenter.prevent
      >
        <template #item="{ element }">
          <div class="element">
            {{ element.name }}
          </div>
        </template>

        <template #footer>
          <div role="group">
            <base-button @click="add">+</base-button>
          </div>
        </template>
      </draggable>
    </div>

    <!--2 column-->
    <div class="column">
      <h3>UX</h3>
      <draggable
        :list="list2"
        group="a"
        item-key="name"
        @dragover.prevent
        @dragenter.prevent
      >
        <template #item="{ element }">
          <div class="element">
            {{ element.name }}
          </div>
        </template>

        <template #footer>
          <div role="group">
            <base-button @click="add2">+</base-button>
          </div>
        </template>
      </draggable>
    </div>

    <!--3 column-->
    <div class="column">
      <h3>Engineering</h3>
      <draggable :list="list3" group="a" item-key="name">
        <template #item="{ element }">
          <div class="element">
            {{ element.name }}
          </div>
        </template>

        <template #footer>
          <div role="group">
            <base-button @click="add3">+</base-button>
          </div>
        </template>
      </draggable>
    </div>
    <!--4 column-->
    <div class="column">
      <h3>Admin</h3>
      <draggable :list="list4" group="a" item-key="name">
        <template #item="{ element }">
          <div class="element">
            {{ element.name }}
          </div>
        </template>

        <template #footer>
          <div role="group">
            <base-button @click="add4">+</base-button>
          </div>
        </template>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import BaseButton from "./UI/BaseButton.vue";
let id = 1;
export default {
  components: {
    draggable,
    BaseButton,
  },
  data() {
    return {
      list: [
        { id: 0, name: "Katherine" },
        { id: 1, name: "David" },
        { id: 2, name: "Dorian" },
        { id: 3, name: "Daniel" },
      ],
      list2: [
        { id: 4, name: "Greg" },
        { id: 5, name: "Val" },
        { id: 6, name: "Ming" },
      ],
      list3: [
        { id: 7, name: "Tara" },
        { id: 8, name: "Husein" },
      ],
      list4: [{ id: 9, name: "Nicky" }],
    };
  },
  methods: {
    add: function () {
      this.list.push({ name: "1 " + id, id: id++ });
    },
    add2: function () {
      this.list2.push({ name: "2 " + id, id: id++ });
    },
    add3: function () {
      this.list3.push({ name: "3 " + id, id: id++ });
    },
    add4: function () {
      this.list4.push({ name: "4 " + id, id: id++ });
    },
  },
};
</script>
<style scoped>
.card {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-column-gap: 2rem;
}

.column {
  display: relative;
  width: 100%;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  margin: 2rem auto;
  background-color: rgb(232, 236, 238);
}

.btn {
  display: flex;
  justify-content: center;
}

.element {
  border-radius: 5px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 2rem auto;
  padding: 1rem 1rem;
  background-color: rgb(249, 250, 250);
}

.sortable-ghost {
  color: rgb(185, 185, 185);
  overflow: hidden;
  background-color: rgb(185, 185, 185);
}
</style>
