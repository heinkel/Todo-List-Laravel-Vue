<template>
    <div>
        <div v-for="(task, index) in tasks" :key="index">
            <list-view :task="task"
                class="task"
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
        background:palevioletred;
        padding: 5px;
        margin-top: 5px;
    }
</style>


