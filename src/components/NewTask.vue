<template>
    <div id="new-task">
        <input class="form-element" type="text" v-model="newTask" placeholder="Nova tarefa?"
        @keydown.13="inputTask">
        <button class="form-element"  @click="inputTask">+</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTask: '',
        }
    },
    methods: {
        inputTask() {
            if (this.newTask) {
                this.$emit('newTask', this.newTask)
                this.newTask = ''
            }
        }
    },
}
</script>

<style scoped>
#new-task {
    margin: 15px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2); 
}
.form-element {
    outline: none;
    border: none;
    padding: 5px 10px 8px;
    color: #fff;
    transition: all 0.1s ease-out;
}
input.form-element {
    width: 350px;
    background: #fff2;
    border-top-left-radius: 5px;
    border-bottom-left-radius: 5px;
}
#new-task button {
    border-left: none;
    background-color: #2196f3;
    cursor: pointer;
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
}
#new-task button:hover {
    background-color: #007ce2
}
</style>
