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
        <h5 class="modal-title" id="exampleModalLabel">Edit Person</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
         <form  class="add-form">
    <div class="form-control">
      <label>firstName</label>
      <input type="text" name="firstName"  v-model="firstName" placeholder="Add firstName" />
    </div>
 
    <div class="form-control">
      <label>lastName</label>
      <input type="text" name="lastName" v-model="lastName" placeholder="Add lastName" />
    </div>
     <div class="form-control">
      <label>Email</label>
      <input type="email" name="email" v-model="email" placeholder="Add email" />
      
    </div>

    
  </form>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="onClick" data-dismiss="modal">Save changes</button>
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
            console.log(this.person.id)
            this.$emit('update-Person',{id:this.person.id,newValue})
        }
    }
    
}
</script>