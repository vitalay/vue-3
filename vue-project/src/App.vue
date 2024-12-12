<template>
  <div class="container-fluid">
    <h1>App</h1>
    <!-- Если my-component нужен, то он должен быть зарегистрирован -->
    <my-component />
    
    <MyNotes
      v-for="(note, index) in notes"
      :key="index"
      :task="note.task"
      :time="note.time"
      :id="note.id"
    />
  </div>
</template>

<script>
import MyNotes from './MyNotes.vue'; // Убедись, что этот компонент существует и находится в правильном пути

export default {
  data() {
    return {
      notes: [
        { task: 'Почистить зубы', id: 1, time: '12:00' },
        { task: 'Покушать', id: 2, time: '13:00' },
        { task: 'Сходить на работу', id: 3, time: '14:00' },
      ],
    };
  },
  components: {
    MyNotes,
  },
};
</script>
