

<template>
  <div class="container-fluid">
  <h1>App</h1>
<my-component />
<MyNotes v-for="note in notes" v-bind:key="note" v-bind:oneNote="note"   />  
  </div>
  

</template>


<script>
import MyNotes from './MyNotes.vue';

 
export default {

  data() {
   
    return {
     notes: ['Почистить зубы', 'Покушать', 'Сходить на работу'] //notes примичание
    }
  },

   components: {
     MyNotes
   }
   
 }


</script>
 

