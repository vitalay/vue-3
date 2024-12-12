<template>
  <div>
    <h2>Заметка: №{{ id }} {{ task }} {{ time }}</h2>
    <strong>Прочитано</strong>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: String,
      required: true,
      default: "Отсутствует заметка",
      validator(value) {
        if (typeof value === "string") {
          return true;
        }
      },
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
      validator(value) {
        if (typeof value === "number") {
          return true;
        }
      },
    },
  },

  data() {
    return {};
  },
};
</script>

<style></style>
