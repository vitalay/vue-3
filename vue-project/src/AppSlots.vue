<template>
    <div>
       <ul>
        <li v-for="(data, index) in slotsData" :key="data">
              <slot :item="data" :i="index"></slot>
        </li>
       </ul> 
      
    
    </div>
 
</template>

<script>
export default {
    data() {
        return {
            slotsData: [
                "a",
                "b",
                "c",
                "d"
        ]
        }
    }

}
</script>

<style>

</style>