<template>
    <div id="progress">
        <h1>Tarefas</h1>
        <div id="progress-bar">
            <span>{{ progress }}%</span>
            <div id="progress-bar-content"
            :style="{width: progress + '%'}">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        progress: { type: Number, required: true }
    },
}
</script>

<style scoped>
#progress {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 90vw;
    height: 30vh;
}
#progress h1 {
    font-weight: lighter;
}
#progress-bar {
    width: 80%;
    height: 15px;
    margin-bottom: 20px;
    border-radius: 5px;
    background: #fff2;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
}
#progress-bar-content {
    position: absolute;
    background-color: seagreen;
    border-radius: 5px;
    height: 100%;
    align-self: flex-start;
    transition: all 0.1s ease-out;
}
#progress-bar span {
    z-index: 1;
    font-size: 0.8em;
    font-weight: bold;
}
</style>