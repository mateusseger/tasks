<template>  
    <div id="task"
        :class="stateClass" 
        @click="$emit('taskChangeState', task)">
        <span class="task-remove" @click.stop="$emit('taskRemove', task)">x</span>
        <p>{{task.desc}}</p>
    </div>
</template>

<script>
export default {
    props: {
        task: { type: Object, required: true }
    },
    computed: {
        stateClass() {
            return {
                finished: this.task.status,
                unfinished: !this.task.status
            }
        }
    }
}
</script>

<style>
#task {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 15px;
    padding: 15px;
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    border-radius: 5px;
    position: relative;
    overflow: auto;
    transition: all 0.1s ease-out;	
    cursor: pointer;
    user-select: none;
    font-weight: bold;
}
#task:hover {
    transform: scale(1.1);
}
.task-remove {
    font-size: 0.9rem;
    position: absolute;
    right: 5px;
    top: 5px;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    transition: all 0.1s ease-out;	
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
}
.finished {
    background-color: seagreen;
    border-left: 10px solid rgb(19, 107, 57);
    text-decoration: line-through;
    color: #fff
}
.unfinished {
    background-color: tomato;
    border-left: 10px solid rgb(172, 77, 60);
}
.finished .task-remove {
    background-color: rgb(19, 107, 57);
}
.unfinished .task-remove {
    background-color: rgb(172, 77, 60);
}
.no-task {
    font-size: 1.5rem;
}
</style>