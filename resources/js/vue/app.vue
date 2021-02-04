<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo List</h2>

            <add-task-form />
        </div>

    </div>
</template>

<script>
import addTaskForm from "./addTaskForm"
import listView from "./listView"
export default {
    components: {
        addTaskForm,
        listView

    }

}
</script>
<style  scoped>
    .todoListContainer {
        width: 350px;
        margin: auto;
    }
    .heading {
        background:#121013;
        padding: 10px;

    }

    #title {
        text-align: center;
        color: #ffe227;
    }
</style>
