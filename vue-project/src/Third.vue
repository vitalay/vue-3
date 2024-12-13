<template>
  <h1>THIRD: {{ time }}</h1>

<ul>
    <li v-for="item in info" v-bind:key="item.id" > {{ item.task }}</li>
</ul>

</template>

<script>
export default {
props: ['time'],
inject: ['info']
}
</script>

<style>

</style>