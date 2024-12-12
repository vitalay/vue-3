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
      :wasTaskRead="note.wasTaskRead"
      :isOpen="note.isOpen"
      @countTaskOpen="note.wasTaskRead++"
    />

    <app-slots>
    
      <template v-slot="slotProps">
        <p>{{ slotProps.i }}: {{ slotProps.item }}</p>
      
      </template>
      
  
    </app-slots>
  </div>
</template>

<script>
import MyNotes from "./MyNotes.vue"; // Убедись, что этот компонент существует и находится в правильном пути
import AppSlots from "./AppSlots.vue";
export default {
  data() {
    return {
      notes: [
        {
          task: "Почистить зубы",
          id: 1,
          time: "12:00",
          isOpen: false,
          wasTaskRead: 0,
        },
        {
          task: "Покушать",
          id: 2,
          time: "13:00",
          isOpen: false,
          wasTaskRead: 0,
        },
        {
          task: "Сходить на работу",
          id: 3,
          time: "14:00",
          isOpen: false,
          wasTaskRead: 0,
        },
      ],
    };
  },
  components: {
    MyNotes,
    AppSlots
  },
};
</script>
