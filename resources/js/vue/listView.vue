<template>
    <div>
        <div v-for="(task, index) in tasks" :key="index">

                <list-task :task="task"

                v-on:taskchanged="$emit('reloadlist')"
                />

        </div>
    </div>

</template>

<script>
import  listTask from "./listTask.vue"
export default {
    props:['tasks'],
    components: {
        listTask
    }
}
</script>
<style scoped>
    .task {
        background: white;
        padding:2px;
        align-items: center;
        text-align: center;
        font-weight: 200;
        font-size: .75rem;
        margin:auto;
        width: 75%;
        height: 1rem;
        color:black;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
 /**   .task:after {
  content: 'Task Item';

}*/
</style>


