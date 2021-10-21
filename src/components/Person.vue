<template>
        <div className="contact-card">
            <img src="https://bootdey.com/img/Content/avatar/avatar1.png" alt="avatar" className="avatar" />
            <h3>{{person.firstName}}</h3>
            <span>{{person.lastName}}</span>
            <span>Email :  {{person.email}}</span>
            <div className="delete-edit-btns">
                <i class="fas fa-times" @click="$emit('deletePerson',person.id)"></i>
                <Edit @editPerson="$emit('editPerson',id,newValue)" :person="person" />
            </div>
        </div>
</template>

<script>
import Edit from './Edit.vue'
export default {
    name:"Person",
    props:{
        person:Object
},
components:{
  Edit
},
emits:['editPerson']
}

</script>
<style>
.contact-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #bcd0d1;
  border: 5px solid #9cb0b1;
  border-radius: 20px;
  width: 200px;
  height: 300px;
  margin: 20px;
  padding: 20px;
}

.avatar {
  width: 40px;
  margin: 20px;
}

.delete-edit-btns {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}

.delete-edit-btns img {
  width: 50px;
  margin: 10px;
  cursor: pointer;
}
.delete-edit{
  color:white;
  cursor: pointer;;
}
</style>