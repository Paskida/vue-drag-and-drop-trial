<template>
  <div>
    <div v-if="open" class="backdrop" @click="$emit('close')"></div>
    <transition name="modal">
      <dialog open v-if="open">
        <div class="form-control">
          <label for="name">Add Task:</label>
          <input id="name" name="name" type="name" ref="nameInput" />
          <p v-if="inputIsInvalid">Please, enter a valid Task</p>
          <base-button @click="submitName">Add</base-button>
        </div>
      </dialog>
    </transition>
  </div>
</template>

<script>
import BaseButton from "./UI/BaseButton.vue";
export default {
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  components: {
    BaseButton,
  },
  props: ["open"],
  emits: ["close"],
  inject: ["addTask"],
  methods: {
    submitName() {
      const enteredName = this.$refs.nameInput.value;
      if (enteredName.trim() === "") {
        this.inputIsInvalid = true;
        return;
      }
      this.addTask(enteredName);
    },
  },
};
</script>

<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: 10;
  background-color: rgba(0, 0, 0, 0.75);
}

dialog {
  position: fixed;
  top: 30vh;
  width: 30rem;
  left: calc(50% - 15rem);
  margin: 0;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  border-radius: 12px;
  padding: 1rem;
  background-color: white;
  z-index: 100;
  border: none;
}

.form-control {
  margin: 1rem 0;
  text-align: center;
  display: flex;
  flex-direction: column;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
  margin: 1rem 0;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.modal-enter-active {
  animation: modal 0.3s ease-out;
}

.modal-leave-active {
  animation: modal 0.3s ease-in reverse;
}

p {
  color: grey;
}

@keyframes modal {
  from {
    opacity: 0;
    transform: translateY(-50px) scale(0.9);
  }

  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}
</style>
