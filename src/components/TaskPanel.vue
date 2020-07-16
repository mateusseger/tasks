<template>
    <div id="task-panel">
        <template v-if="tasks.length">
            <Task v-for="(task, i) in tasks" :key="task.desc" :task="task"
                @taskRemove="$emit('taskRemove', i)"
                @taskChangeState="$emit('taskChangeState', i)">
            </Task>  
        </template>
        <h1 v-else class="no-task">Sua vida esta em dia :)</h1>     
    </div>
</template>

<script>
import Task from '@/components/Task.vue'

export default {
    props: {
        tasks: { type: Array, required: true}
    },
    components: {
        Task
    }
}
</script>

<style scoped>
#task-panel {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    margin: 15px;
    width: 90vw;
}
#task-panel h1 {
    font-weight: lighter;
    background-color: #fff2;
    padding: 15px;
    border-radius: 5px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    border-bottom: 5px solid #2196f3;
    transition: all 0.1s ease-out;
    margin: 80px;
}
#task-panel h1:hover {
    border-color: #007ce2
}
</style>