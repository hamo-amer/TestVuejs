<template>
    <header>
        <Button @toggle-add-person="$emit('toggle-add-person')"
          
         :text="showAddPerson ? 'Close':'Add Person'" />
    </header>
</template>
<script>
import Button from './Button.vue'

export default {
    name:'Header',
    components:{
        Button
    },
    props:{
      showAddPerson:Boolean
    },
    emits:['toggle-add-person']
    }
</script>
<style scoped>
header{
    display: flex;
    justify-content: space-around;
    align-items: center;
    }
</style>
