<template>
      <form @submit="onSubmit" class="add-form">
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

    <input type="submit" value="Save" class="btn btn-block" />
  </form>
</template>
<script>
export default {
    name:'AddPerson',
    data(){
        return {
            firstName:"",
            lastName:"",
            email:""
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()
            const newPerson={
                firstName:this.firstName,
                lastName:this.lastName,
                email:this.email
            }
            this.$emit('addPerson',newPerson)
            this.firstName=""
            this.lastName=""
            this.email=""
            this.$emit('toggleAddPerson')
        }
    }
    
}
</script>
<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 80%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>