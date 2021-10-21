<template>
<Header :showAddPerson="showAddPerson" @toggle-add-person="toggleAddPerson"  />
<div v-if="showAddPerson">
<AddPerson @addPerson="addPerson" @toggleAddPerson="toggleAddPerson" />
</div>
 <Persons :persons="persons" @deletePerson="deletePerson" @editPerson="editPerson" />
</template>

<script>
import Header from './components/Header.vue'
import Persons from './components/Persons.vue'
import AddPerson from './components/AddPerson.vue'

export default {
  name: 'App',
  components: {
   Persons,Header,AddPerson
  },
  data(){
    return {
      persons:[],
      showAddPerson:false
    }
  },
  methods:{
      toggleAddPerson() {
      this.showAddPerson = !this.showAddPerson
    },
    async getAllPersons(){
      const res=await fetch('api/persons')
      const data=await res.json()
      return data
    },
    async addPerson(person){
      const res=await fetch('api/persons',{
        method:'POST',
        headers:{
          'Content-Type':'application/json'
        },
        body:JSON.stringify(person)
      })
      const data=await res.json()
      this.persons=[...this.persons,data]
    },
    async deletePerson(id){
      const res=await fetch(`api/persons/${id}`,{
        method:'DELETE'
      })
      res.status===200 ? this.persons=this.persons.filter(person=>person.id!==id):alert('Error deleting')
    },
    async editPerson(edit){
      const personToUpdate=await this.getPerson(edit.id)
      console.log(personToUpdate)
      const upDatePerson={...personToUpdate,...edit.newValue}
      const res=await fetch(`api/persons/${edit.id}`,{
        method:'PUT',
        headers:{
          'Content-Type':'application/json'
        },
        body:JSON.stringify(upDatePerson)
      })
      const data=await res.json()
      this.persons=this.persons.map(person=>person.id===edit.id ? data:person)
    },
    async getPerson(id){
      const res=await fetch(`api/persons/${id}`)
      const data=await res.json()
      return data
    }
  },
  async created(){
    this.persons=await this.getAllPersons()
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
width: 100%;
}
</style>
