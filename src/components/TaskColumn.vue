<template>
  <div class="card">
    <div v-for="task in tasks" :key="task.id" class="column">
      <h3>{{ task.title }}</h3>
      <draggable
        id="first"
        data-source="juju"
        :list="task.names"
        :move="checkMove"
        group="a"
        item-key="name"
      >
        <template #item="{ element }">
          <div class="element">
            {{ element.name }}
          </div>
        </template>

        <template #footer>
          <div role="group" class="btn">
            <base-button @click="showNameAdd(task.id)">+</base-button>
          </div>
        </template>
      </draggable>
      <add-task @close="hideNameAdd" :open="addIsVisible"> </add-task>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import BaseButton from "./UI/BaseButton.vue";
import AddTask from "./AddTask.vue";
/* ; */
export default {
  emits: ["taskid"],
  components: {
    draggable,
    BaseButton,
    AddTask,
  },
  provide() {
    return {
      addTask: this.addTask,
    };
  },
  data() {
    return {
      addIsVisible: false,
      taskid: null,
      id: 10,
      tasks: [
        {
          title: "Not Urgent",
          id: 0,
          names: [
            { id: 0, name: "Answer the letter" },
            { id: 1, name: "Send the package" },
            { id: 2, name: "Buy coffee" },
            { id: 3, name: "Watch the video" },
          ],
        },
        {
          title: "Urgent",
          id: 1,
          names: [
            { id: 4, name: "Call mum" },
            { id: 5, name: "Check post" },
            { id: 6, name: "Cook a dinner" },
          ],
        },
        {
          title: "In process",
          id: 2,
          names: [
            { id: 7, name: "Read the book" },
            { id: 8, name: "Cook breakfast" },
          ],
        },
        {
          title: "Done",
          id: 3,
          names: [{ id: 9, name: "Wash floors" }],
        },
      ],
    };
  },
  methods: {
    checkMove(evt) {
      const activeCol = document.querySelector(".active.column");

      if (activeCol) {
        activeCol.classList.remove("active");
      }
      evt.to.closest(".column").classList.add("active");
    },
    showNameAdd(taskid) {
      this.addIsVisible = true;
      this.taskid = taskid;
      console.log(this.taskid);
    },
    hideNameAdd() {
      this.addIsVisible = false;
      this.taskid = null;
    },
    addTask(name) {
      const newName = {
        id: this.id++,
        name: name,
      };
      this.tasks[this.taskid].names.push(newName);
      this.addIsVisible = false;
      this.taskid = null;
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
  display: block;
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

.active {
  border: 3px solid rgb(255, 0, 242);
}

.form-control {
  margin: 1rem 0;
}
</style>
