<template>
    <div class="task">
        <input
            type="checkbox"
            @change="updateCheck()"
            v-model="task.is_done"
        />
            <span :class="[task.is_done ? 'is_done' : '' , 'taskText']">{{ task.name }}</span>
            <button @click="removeTask()" class="trash-button">

            </button>
    </div>
</template>
<script>
export default {
    props:["task"]
}
</script>

<style scoped>
    .completed {
        text-decoration: line-through;
        color: #999;
    }

    .taskText {
        width: 100%;
        margin-left: 20px;
    }

    .task{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .trash-button {
        background: whitesmoke;
        border: none;
        color: red;
        outline: none;

    }
</style>
