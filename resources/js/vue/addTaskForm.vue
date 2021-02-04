
<template>
    <div class="addTask">
         <input type="text" v-model="task.name" placeholder="Add new task" />
         <font-awesome-icon
            icon="plus-square"
            @click="addTask()"
            :class="[task.name ? 'active' : 'inactive' , 'plus']"
        />
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
                this.task.name  ==  "";
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
}
input {
    background: #ffe227 ;
    border: 1px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
    width: 100%;
    color:#4d375d;
    font-weight: 900;

}
.plus{
    font-size: 20px;
}
.active{
    color: #eb596e;
}
.inactive{
    color:#4d375d;
}
</style>
