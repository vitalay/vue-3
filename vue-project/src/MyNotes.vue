<template>
  <div>
    <h2 v-if="isTaskOpen"
    v-bind:class="wasTaskRead < 2 ? 'bg-success' : 'bg-danger'"
    >Задание: №{{ id }} {{ task }} </h2>
    <p>{{ time }}</p>
    <button class="btn btn-success" v-on:click="openTask"> Задание прочитано </button>
    <strong>Прочитано: {{ wasTaskRead }}</strong>
    <Third />
  </div>
</template>

<script>
import Third from './Third.vue'

export default {
  props: {
    task: {
      type: String,
      required: true,
      default: "Отсутствует заметка",

    },

    time: {
      type: String,
      required: true,
      default: "Отсутствует время",
   
    },
    id: {
      type: Number,
      required: true,
      default: 0,
    
    },
    wasTaskRead : {
      type: Number,
    },
    isOpen: {
      type: Boolean,
    },

  },

  data() {
    return {
        isTaskOpen: this.isOpen
    };
  },

  methods: {
    openTask() {
      this.isTaskOpen = !this.isTaskOpen;
      if (this.isTaskOpen) {
        this.$emit("countTaskOpen", this.id);
      }
    },
  },
  components: {
    Third
  }
};
</script>

<style></style>
