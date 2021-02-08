<template>
    <div class="task">
        <input
            type="checkbox"
            @change="updateCheck()"
            v-model="task.is_done"
        />
            <span :class="[task.is_done ? 'is_done' : '' , 'taskText']">{{ task.name }}</span>

            <button @click="removeTask()" class="trashbutton" >

            </button>
    </div>
</template>
<script>
export default {
    props:["task"],
    methods: {
        updateCheck() {
            axios.put('api/task/' + this.task.id,
            { task: this.task
            })
            .then( response => {
                if (response.status == 200)
                    {
                        this.$emit('taskchanged')
                    }
            })
            .catch( error => {
                console.log(error);
            })
            },
            removeTask(){
                axios.delete('api/task/' + this.task.id)
                .then( response => {
                    if (response == 200 ) {
                        this.$emit('taskchanged');
                        this.$forceUpdate();
                    }
                })
                .catch( error => {
                    console.log(error);
                })
            }
    }
}
</script>

<style scoped>
    .is_done {
        text-decoration: line-through;
        color: #999;
    }

    .taskText {
        width: 100%;

    }

    .task{
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .trashbutton {
        background: rgb(255, 146, 146);
        border: none;
        color: black;
        outline: none;
        height: .8rem;
        width: .8rem;
        transform: rotate(45deg);
        margin-right: 10px;

    }

</style>
