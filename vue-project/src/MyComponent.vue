<template>
  <div>
    <h1>Счетчик: {{ count }}</h1>
    <button class="btn btn-primary" @click="count++">Прибавить</button>
    <button class="btn btn-danger" @click="count--">Убавить</button>

    <hr />

    <input
      type="text"
      :placeholder="clue"
      v-model="inputValue"
      v-on:keypress.enter="addNewNote"
    />
    <div>
      <p>Введенное значение: {{ inputValue }}</p>
      <div>Всего заметок: {{ notes.length }}</div>

      <div v-if="notes.length === 1">
        сейчас одна заметка
        <ul class="list-group">
          <li
            class="list-group-item"
            v-for="(note, index) in notes"
            :key="index"
          >
            {{ note }}
            <br />
            <button class="btn btn-danger" v-on:click="deleteNote(index)">
              Удалить
            </button>
          </li>
        </ul>
      </div>
      <ul class="list-group" v-else-if="notes.length !== 0">
        <li class="list-group-item" v-for="(note, index) in notes" :key="index">
          {{ note }}
          <br />
          <button class="btn btn-danger" v-on:click="deleteNote(index)">
            Удалить
          </button>
        </li>
      </ul>
      <div v-else>Заметок нет</div>
      <div>{{ calculatesNotes }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      clue: "Введите что-нибудь",
      inputValue: "",
      notes: ["one", "two", "three"],
    };
  },
  methods: {
    addNewNote(event) {
      this.notes.push(event.target.value);
      event.target.value = "";
    },
    deleteNote(index) {
      this.notes.splice(index, 1);
    },
  },
  computed: {
    calculatesNotes() {
      console.log("calculatesNotes", this.notes.length * 5);
      return this.notes.length * 5;
    },
  },
  watch: {
    inputValue(value) {
      console.log("value", value);
      if (value.length === 10) {
        this.inputValue = 0;
      }
    },
  },
};
</script>

<style scoped></style>
