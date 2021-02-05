<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo List</h2>

            <add-task-form/>
             <div class="Tlist">

                <list-view :tasks="tasks" />
             </div>

        </div>

    </div>
</template>

<script>
import addTaskForm from "./addTaskForm"

import listView from "./listView"

export default {
    components: {
        addTaskForm,
        'list-view': listView

    },
    data: function() {
        return {
            tasks: []
        }
    },
    methods: {
        getTask() {
            axios.get('api/tasks')
            .then( response => {
                this.tasks = response.data
            })
            .catch( error => {
                console.log( error );
            })
        }
    },
    created() {
        this.getTask();
    }

}
</script>
<style  scoped>
    .todoListContainer {
        width: 350px;
        margin: auto;
    }
    .heading {
        background: #ffe227;
        padding: 10px;
        border-radius: 12px;
    }
    /**template{
        background-color: black;
    }*/
    #title {
        text-align: center;
        color: #121013;
    }.Tlist {
        margin-top: 10px;
        width:100%;
    }


</style>
