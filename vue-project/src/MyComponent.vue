

<template>
  <div>
<h1>Счетчик: {{ count }} </h1>
<button class="btn btn-primary" @click="count++" >Прибавить</button>
<button class="btn btn-danger" @click="count--">Убавить</button>
</div>
<hr />

<input type="text" 
:placeholder="clue"
 v-model="inputValue"
 v-on:keypress.enter="addNewNote"
  />
<p>Введенное значение: {{ inputValue }}</p>

<ul class="list-group" v-if="notes.length !== 0">
  <li class="list-group-item" v-for="(note, index) in notes" :key="index" >{{ note }}
  <br />
  <button class="btn btn-danger" v-on:click="deleteNote(index)">Удалить</button>
</li>
</ul>

</template>

<script>
export default {
  
  data() {
    return {
      count: 0,
      clue: "Введите что-нибудь",
      inputValue: "",
      notes: [ 
         'one',
         'two',
         'three',
       
      ]
    };
  },
  methods: {
     addNewNote(event) {
       this.notes.push(event.target.value);
       event.target.value = "";
     },
     deleteNote(index) {
       this.notes.splice(index, 1);
      }
      
    },
    };

</script>

<style scoped>
 
 


</style>

