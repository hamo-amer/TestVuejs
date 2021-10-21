<template>
   <!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  <!-- <i class="fas fa-edit" ></i> -->
  edit
</button>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
         <form  class="add-form">
    <div class="form-control">
      <label>firstName</label>
      <input type="text" name="text" v-model="firstName" placeholder="Add firstName" />
    </div>
 
    <div class="form-control">
      <label>lastName</label>
      <input type="text" name="text" v-model="lastName" placeholder="Add lastName" />
    </div>
     <div class="form-control">
      <label>Email</label>
      <input type="email" name="text" v-model="email" placeholder="Add email" />
      
    </div>

    
  </form>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="onClick" >Save changes</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
    name:"Edit",
    props:{
        person:Object
    },
    data(){
        return {
           firstName:"",
            lastName:"",
            email:""
        }
    },
    methods:{
        onClick(){
            const newValue={
                firstName:this.firstName,
                lastName:this.lastName,
                email:this.email
            }
            
            this.$emit('editPerson',this.person.id,newValue)
            console.log(newValue)
        }
    }
    
}
</script>