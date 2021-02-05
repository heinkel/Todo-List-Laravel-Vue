<template>
    <div>
        <div v-for="(task, index) in tasks" :key="index">
            <div class="task">
                {{ task.name }}
            </div>
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
        margin:auto;
        width: 90%;
        height: 1rem;
        color:black;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;


    }
 /**   .task:after {
  content: 'Task Item';

}*/
</style>


