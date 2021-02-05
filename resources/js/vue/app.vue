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

        padding: 10px;
        border-radius: 12px;
        background: #7474BF;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #348AC7, #7474BF);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #348AC7, #7474BF); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

    }
    /**template{
        background-color: black;
    }*/
    #title {
        text-align: center;
        color: white;
    }.Tlist {
        margin-top: 10px;
        width:100%;
    }


</style>
