
<template>
    <div class="addTask">
         <input type="text" v-model="task.name" placeholder="Add new task" />
         <button
            @click="addTask()"
            :class="[task.name ? 'active' : 'inactive' , 'plus']"
        >Add</button>
    </div>
</template>
<script>
export default {
    data: function () {
        return {
            task: {
                name: ""
            }
        }
    },
    methods: {
        addTask() {
            if(this.task.name == ''){
                return;
                }
        axios.post('api/task/store',{
            task: this.task
        })
        .then( response => {
            if(response.status ==   201 ){
                this.task.name  =  "";
                this.$emit('reloadlist');
            }
        })
        .catch( error => {
            console.log(error);
        })
        }
    }
}
</script>
<style  scoped>
.addTask {
    display: flex ;
    justify-content: center;
    align-items: center;
    position:relative;
    margin-top: .5rem;
}
input {
    background: #eb596e;
    border: 2px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
    width: 80%;
    color:rgb(228, 222, 222) ;
    font-weight: 900;
    border-radius: 12px;
    border:1px solid black;
}

button{
    outline: none;
    height: 1.6rem;
    border-radius: 12px;

}
input::placeholder {
  color: white;
  opacity: 1;
}



.plus{
    font-size: .85rem;
    color:white;

}
.active{
    background-color: #eb596e;
}
.inactive{
    background-color:#4d375d;
}


</style>
