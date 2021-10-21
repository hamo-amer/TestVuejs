<template>
   <div class="container">
        <div class="row justify-content-center">
          <div class="col-12 col-sm-8 col-lg-6">
            <!-- Section Heading-->
            <div class="section_heading text-center wow fadeInUp" data-wow-delay="0.2s" style="visibility: visible; animation-delay: 0.2s; animation-name: fadeInUp;">
              <h2>List of Persons</h2>
              <div class="line"></div>
            </div>
          </div>
        </div>
        <br/>
        <br/>
        <div class="list">
        <div class="row" :key="person.id" v-for="person in persons"  >
           <Person :person="person" @deletePerson="$emit('deletePerson',person.id)" @edit-Person="$emit('updatePerson',$event)" />
        </div>
        </div>
   </div>
</template>

<script>
import Person from './Person.vue'
export default {
    name:"Persons",
    props:{
        persons:Array
    },
    components:{
        Person
         },
         emits:['deletePerson','updatePerson']
}
</script>
<style scoped>
.list{
    width: 100%;
    display: flex;
    justify-content: space-evenly;
    flex-wrap:wrap;
}

</style>