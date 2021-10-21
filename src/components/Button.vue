<template>
    <button @click="$emit('toggle-add-person')" class="btn">{{text}}</button>
</template>
<script>


export default{
  name:"Button",
  props:{
    text:String
  },

  methods:{
    onClick(){
this.$emit('toggle-add-person')
    }
  }
}
</script>
<style  scoped>
.btn{
  padding: 5px 20px;
  background-color: green;
  color:white;
  border-radius: 5px;
}
</style>
