<template>
  <div>
    <h1>Счетчик: {{ count }}</h1>
    <button class="btn btn-primary" @click="count++">Прибавить</button>
    <button class="btn btn-danger" @click="count--">Убавить</button>

    <hr />
     <h2 v-bind:class="notes.length >5 ? 'first' : 'second'">Ввод</h2>
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
      <ul 
      v-bind:class="{yellow: true, green: notes.length > 5}"
      v-else-if="notes.length !== 0"
      >
      <li v-bind:class="['list-group-item', 'yellow', {'green': notes.length > 5}]"  v-for="(note, index) in notes" :key="index">
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

<style scoped>
.first {
  background: rgb(30, 255, 0);
}
.second {
  background: rgb(255, 0, 76);
}
.yellow {
  background: rgb(255, 230, 0);
}
.green {
  background: rgb(43, 255, 0);
}




</style>
